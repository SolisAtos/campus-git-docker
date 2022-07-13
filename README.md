# Commands to run the Official Docker Hello World container

From https://hub.docker.com/_/hello-world

First make sure that Docker Desktop is running to avoid the `error during connect: This error may indicate that the docker daemon is not running.` error.

## Pulling the image
```sh
docker pull hello-world
```

## Running the container
```sh
docker run hello-world
```

## Obtained output
Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

## Conclusion
The output obtained shows that the container ran successfuly.

# Commands to run the SQL Server container

To test the connection make sure you have [SQL Server Management Studio](https://docs.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-ver16) installed.

## Pulling the image
```sh
docker pull mcr.microsoft.com/mssql/server
```

## Running the container
For the `$pwd` to work make sure that you run the command in powershell.


```powershell
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=Passw0rd" -p 1433:1433 -v $pwd/mssql/data:/var/opt/mssql/data -v $pwd/mssql/log:/var/opt/mssql/log -v $pwd/mssql/secrets:/var/opt/mssql/secrets -d mcr.microsoft.com/mssql/server
```

The `-p 1433:1433` maps our port 1433 to the container's port 1433, allowing us to connect to it using SQL Server Management Studio.

The persistence is done by the `-v $pwd/mssql/data:/var/opt/mssql/data -v $pwd/mssql/log:/var/opt/mssql/log -v $pwd/mssql/secrets:/var/opt/mssql/secrets`, which maps the data, log, and secrets directories to our host machine, allowing the database to persist even if the container is deleted.

## Connecting to SQL in the container
In SQL Server Management Studio use `.,1433` in the "Server name", `sa` in the "login" field and the password chosen in the `MSSQL_SA_PASSWORD` environment variable in the "password" field. In this example the password is `Passw0rd`.

If the connection is successful the SQL Server Management Studio will load in the Object Explorer (right hand side) the properties of the database.

# Commands to upload changes to a remote git repository
First we have to create the remote repository. In this example I'm using GitHub.

Then we have to create a local repository. To do this, open the directory of the project that you want to add version control to and run the `git init` command.

Now we have to add the remote repository to the local repository by executing the following commands:

```sh
git remote add origin https://github.com/SolisAtos/campus-git-docker.git
git branch -M main
git push -u origin main
```

Make sure to replace `https://github.com/SolisAtos/campus-git-docker.git` with the remote repository created in GitHub.

Now that the remote repository is added, we are ready to upload some changes.

Add or modify one or more files that you want to track and then add the changes using the `git add .`. Here the `.` is telling git to stage all changes that have been done. Another option is to replace `.` with a specific filename of the specific file you want to track.

Once the changes have been staged, you need to commit them using `git commit -m "Message"` where `"Message"` is a short description of the changes that you made.

Now we are ready to push the changes to the remote repository. The easiest way is to just run the `git push` command, which will automatically push to `origin` the current branch. To have greater control of the push, you can run `git push origin main` and substitute `origin` and `main` for the specific remote and branch that you want to push to the remote repository.

After running the last command, all changes will be uploaded to the remote repository.