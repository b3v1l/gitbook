# terraform \(DG\)

## Dropplet

### Create a dropplet

#### provider.tf

```
terraform {
```

```csharp
  required_version = ">= 0.12.0"
  required_providers {
    digitalocean = {
      source = "digitalocean/digitalocean"
    }
    local = ">= 1.2"
  }
}
provider "digitalocean" {
  token = var.do_token
}
```

#### variables.tf

```csharp
variable "do_token" {
  description = "DigitalOcean API Key"
  type        = string
  sensitive   = true
}
```

#### main.tf

```csharp
resource "digitalocean_tag" "project_tag" {
  name = "devopshost"
}

resource "digitalocean_ssh_key" "ssh_key" {
  name       = "Devops SSH Key"
  public_key = file("/home/devops/terraform/key.pub")
}

resource "digitalocean_droplet" "devops_vm_1" {
  image = "ubuntu-20-04-x64"
  name = "offsec0"
  region = "fra1"
  size = "s-2vcpu-2gb-amd"
  tags = [digitalocean_tag.project_tag.id]
  private_networking = true
  ssh_keys = [
    digitalocean_ssh_key.ssh_key.fingerprint
  ]
  connection {
    host = self.ipv4_address
    user = "root"
    type = "ssh"
    agent = false
    timeout = "3m"
    private_key = file("/home/devops/key")
  }
  provisioner "remote-exec" {
    inline = [
      "export PATH=$PATH:/usr/bin",
      "sudo apt-get update",
      "sudo adduser --disabled-password --gecos '' ansible",
      "sudo mkdir -p /home/ansible/.ssh",
      "sudo touch /home/ansible/.ssh/authorized_keys",
      "sudo echo '${file("/home/devops/terraform/key")}' > authorized_keys",
      "sudo mv authorized_keys /home/ansible/.ssh",
      "sudo chown -R ansible:ansible /home/ansible/.ssh",
      "sudo chmod 700 /home/ansible/.ssh",
      "sudo chmod 600 /home/ansible/.ssh/authorized_keys",
      "sudo usermod -aG sudo ansible",
      "sudo echo 'ansible ALL=(ALL) NOPASSWD:ALL' | sudo tee -a /etc/sudoers"
    ]
  }
resource "digitalocean_firewall" "firewall" {
  name = "devopsFW"

  droplet_ids = [digitalocean_droplet.devops_vm_1.id]
  inbound_rule {
    protocol         = "tcp"
    port_range       = "22"
    source_addresses = ["0.0.0.0/0"]
  }
  inbound_rule {
    protocol         = "tcp"
    port_range       = "80"
    source_addresses = ["0.0.0.0/0"]
  }
  inbound_rule {
    protocol         = "tcp"
    port_range       = "443"
    source_addresses = ["0.0.0.0/0"]
  }
  inbound_rule {
    protocol         = "tcp"
    port_range       = "7443"
    source_addresses = ["0.0.0.0/0"]
  }
  outbound_rule {
    protocol         = "udp"
    port_range       = "1-65535"
    destination_addresses = ["0.0.0.0/0"]
  }
  outbound_rule {
    protocol         = "tcp"
    port_range       = "1-65535"
    destination_addresses = ["0.0.0.0/0"]
  }
} 
}

```

#### output.tf

```csharp
output "do_ip" {
  value = digitalocean_droplet.devops_vm_1.ipv4_address
}
```

### Create and start the VM

```csharp
# From the config files folder type
terraform init
terraform plan
terraform apply -auto-approve
```

### Delete the VM

```csharp
terraform destroy -auto-approve 
```

