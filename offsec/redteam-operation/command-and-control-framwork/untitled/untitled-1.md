# SilentTrinity Installation

## Server installation <a id="server-installation"></a>

```csharp
git clone https://github.com/byt3bl33d3r/SILENTTRINITY
apt update && apt upgrade
apt install python3.7 python3.7-dev python3-pip
sudo -H pip3 install -U pipenv
cd SILENTTRINITY
pip3 install -r requirements.txt
pipenv install && pipenv shell
```

### Start the server <a id="start-the-server"></a>

```csharp
python st.py teamserver --port 5000 0.0.0.0 TrinityPassword!
```

## Client Installation <a id="client-installation"></a>

```csharp
git clone https://github.com/byt3bl33d3r/SILENTTRINITY
apt update && apt upgrade
apt install python3.7 python3.7-dev python3-pip
sudo -H pip3 install -U pipenv
cd SILENTTRINITY
pip3 install -r requirements.txt
pipenv install && pipenv shell
```

### Start the client

```csharp
pipenv install && pipenv shell
python st.py client wss://aptclass:PASSWORD@IP:port
```

