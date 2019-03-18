# Containers

## Running, detaching and attaching to containers

Let's run a VS code ! And with a cute name.

```
docker run --name vscode codercom/code-server
```

🤔 but I don't want to be attached to the output... Just CTRL+c to quit and let's remove that container.

```
docker rm vscode
```

🤔 runs but nor good enough

need:

* Port mapping (-p) 
* Volume mapping (-v)
* Allocate a pseudo-tty (-t)


```
docker run -t -p 127.0.0.1:8443:8443 -v "${PWD}:/root/project" --name vscode codercom/code-server --allow-http --no-auth
```

Now let's run a new VsCode container, but in the background with the `-d` flag (`d` as in `detach`).

```
docker run -t -p 127.0.0.1:8443:8443 -v "${PWD}:/root/project" --name vscode -d codercom/code-server --allow-http --no-auth
```

Cool! Now let's check out the vsCode. First you need to sort-of-`ssh` into the container. You don't actually use `ssh`, instead you can _execute_ a command with the interactive mode, like so:

```
docker exec -it vscode
```

OR

```
docker exec -it <container id>
```

Now you're running in the `codercom/code-server` container in the `vscode` container. Toy around and then `exit` to quit.


Now check if it did something:

```
docker logs vscode
```