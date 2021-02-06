# git

## git 

### Own git repo 

```csharp
echo "# python" >> README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin https://github.com/USER/python.git
git push -u origin master
```

### Authentication Methods <a id="change-https-authentication-for-ssh-auth"></a>

```csharp
git remote add origin https://github.com/USER/python.git
```

#### First use

```csharp
git clone repo
git pull
```

#### Make change on files then :

```text
git commit -a -m "My changes"
```

#### then, apply 

```text
git push
```

### Add files <a id="add-files"></a>

```csharp
git add path/to/files or git add . (from where you are)
```

#### Then commit and push

### Check files

```csharp
git status
```

note :

* git add = for new files
* git commit -a = for modifications made in existing files

### Change Branch 

#### checkout the branch

```csharp
git branch
```

#### Change branch

```csharp
git checkout MY_BRANCH
```

### Restore previous change <a id="corriger-et-revenir-&#xE0;-un-ancien-commit"></a>

```csharp
git checkout commit_number nom_du_module
git reverse #du commit    (voir internet)
```

### Start a project 

```csharp
git init
git status
git add file_name
git diff file_name
git commit -m "My text"
```

### List commits 

```csharp
git log
```

### Delete a file

```csharp
git rm --cached MYFILE
git commit --amend -CHEAD
git push -f origin master
```

### ssh key

```text
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_priv_key
```

\`\`

