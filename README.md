# Choreography and Diligence

*Why microservices by default isn't a great bet.*

## Setup

```bash
git clone git@github.com:pkoch/2022-06-08-Choreography-and-Diligence.git
cd 2022-06-08-Choreography-and-Diligence
pnpm i
```

There's a [pre-commit](https://pre-commit.com/) hook to make sure you don't
forget to build before you commit. If you're using pre-commit, run:

```bash
pre-commit install
```

## Code

```bash
pnpm watch & (sleep 1; open slides.html); fg
```

The main file is [slides.md](slides.md).

## Build

The `watch` script adds an auto-reload mechanism to `slides.html`. We don't
want that in our final build.

After you're done editing, run

```bash
pnpm build
```

and commit your files.

## Published

<https://pko.ch/talks/2022-06-08-Choreography-and-Diligence/>
