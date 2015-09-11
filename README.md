# Bower 

[![Bower](https://cdn.rawgit.com/crystal/bower/master/.crystal/icon.svg)](https://hub.crystal.sh/crystal/bower)

official [Bower](http://bower.io) module of [Crystal](https://crystal.sh)


<a name="install"></a>

# Install

First install [Crystal](https://crystal.sh):

```sh
# Choose one:
npm install crystal-cli -g
brew install crystal
git clone https://github.com/crystal/crystal-cli
```

Then use Crystal to install [crystal/bower](https://hub.crystal.sh/crystal/bower):

```sh
crystal install crystal/bower
```

<a name="usage"></a>

# Usage

## ConfigGenerator

Generates a `.bowerrc` file:

```yaml
imports:
  crystal/bower: latest
outputs:
  - generator: bower.ConfigGenerator
    spec:
      directory: app/components/
      analytics: false
      timeout: 120000
      registry:
        search:
          - http://localhost:8000
          - https://bower.herokuapp.com
```

## PackageGenerator

Generates a `package.json` file:

```yaml
imports:
  crystal/bower: latest
outputs:
  - generator: bower.PackageGenerator
    spec:
      name: blue-leaf
      version: 1.2.3
      description: Physics-like animations for pretty particles
      main:
        - js/motion.js
        - sass/motion.scss
      dependencies:
        get-size: ~1.2.2
        eventEmitter: ~4.2.11
      devDependencies:
        qunit: ~1.16.0
      moduleType:
        - amd
        - globals
        - node
      keywords:
        - motion
        - physics
        - particles
      authors:
        - Betty Beta <bbeta@example.com>
      license: MIT
      ignore:
        - '**/.*'
        - node_modules
        - bower_components
        - test
        - tests
```

