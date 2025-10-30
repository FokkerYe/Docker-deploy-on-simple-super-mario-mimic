# Docker-deploy-on-simple-super-mario-mimic
testing deploy


Create and navigate to a directory
```
mkdir mario
cd mario
git clone https://github.com/iam-veeramalla/super-mario-mimic.git

```
Install Node.js package manager
```
apt install npm -y

```
Create .dockerignore
```
cat > .dockerignore <<'EOF'
node_modules
dist
npm-debug.log
Dockerfile
.git
.vscode
.env
EOF

```
Build the Docker image
```
docker build -t super-mario-mimic:latest .

```
. Check the built image
```
docker images | grep super-mario-mimic -n || true

```
Remove any existing container
```
docker rm -f super-mario 2>/dev/null || true

```
Cleans up any previous container named super-mario.
Run the container
```
docker run -d --name super-mario -p 8080:8080 super-mario-mimic:latest

```
Starts the container in detached mode, mapping port 8080 on your host to 8080 in the container.
Verify the container
```
docker ps -a | grep super-mario -n || true
```
Shows the running container.
View logs
```
docker logs -f super-mario
```
Streams container logs — you should see something like:
```
Server running on port 8080
```
Server running on port 8080
Access the app

```
http://<server-ip>:8080
```


