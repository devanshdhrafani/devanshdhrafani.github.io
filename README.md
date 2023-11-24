# Devansh's Portfolio and Blog

Check out my website at: [devanshdhrafani.github.io](https://devanshdhrafani.github.io/)

## Setup

1. Generate Gemfile.lock:

    `docker run --rm -v "$PWD":/usr/src/app -w /usr/src/app ruby:3.2 bundle install`

2. Build Docker image:

    `docker compose -f ./docker/docker-compose.build-image.yml build`

3. Run:

    `docker compose -f ./docker/docker-compose.default.yml up`



## Attribution

- Based on the Jekyll [TeXt Theme](https://github.com/kitian616/jekyll-TeXt-theme).
- [Robot icons created by Hilmy Abiyyu A. - Flaticon](https://www.flaticon.com/free-icons/robot).