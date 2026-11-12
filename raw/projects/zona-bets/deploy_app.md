When you run the container, you'd pass your token and mount a volume like this:

docker run -e TOKEN=your_token_here -v /your/host/path:/data zonabets

The -v flag is what keeps the database persistent across container restarts — without it, all data would be lost every time the container stops.