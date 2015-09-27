# Bower

[![Bower](https://cdn.rawgit.com/crystal/bower/master/.autocode/icon.svg)](https://hub.crystal.sh/crystal/bower)

generator / schema of `bower.json` and `.bowerrc` for [Bower](http://bower.io)

## Install

First install [Autocode](https://crystal.sh):
      
```sh
# Choose one:
npm install autocode-cli -g
brew install autocode # mac users
git clone https://github.com/crystal/autocode-cli
```

Then use Autocode to install [crystal/bower](https://hub.crystal.sh/crystal/bower):

```sh
autocode install crystal/bower
```

## Exports

- [ConfigGenerator](#module-ConfigGenerator) - Generates a `.bowerrc` file.
- [ConfigSchematic](#module-ConfigSchematic) - Schema for `.bowerrc` files.
- [PackageGenerator](#module-PackageGenerator) - Generates a `bower.json` file.
- [PackageSchematic](#module-PackageSchematic) - Schema for `bower.json` files.


### <a name="module-ConfigGenerator"></a> ConfigGenerator
      
Generates a `.bowerrc` file.


#### Example Input

##### .autocode/config.yml

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

#### Example Output

##### .bowerrc

```json
{
	"analytics": false,
	"directory": "app/components/",
	"registry": {
		"search": [
			"http://localhost:8000",
			"https://bower.herokuapp.com"
		]
	},
	"timeout": 120000
}
```



### <a name="module-ConfigSchematic"></a> ConfigSchematic
      
Schema for `.bowerrc` files.



#### Schema

```yaml
type: object
additionalProperties: false
properties:
  analytics:
    type: boolean
  cwd:
    type: string
  directory:
    type: string
  registry:
    type:
      - string
      - object
    properties:
      search:
        type:
          - string
          - array
        items:
          type: string
      register:
        type: string
      publish:
        type: string
  shorthand-resolver:
    type: string
  proxy:
    type: string
  https-proxy:
    type: string
  user-agent:
    type: string
  timeout:
    type: number
  strict-ssl:
    type: boolean
  ca:
    type: string
  color:
    type: boolean
  storage:
    type: object
    properties:
      packages:
        type: string
      registry:
        type: string
      links:
        type: string
      completion:
        type: string
  tmp:
    type: string
  interactive:
    type: boolean
```



### <a name="module-PackageGenerator"></a> PackageGenerator
      
Generates a `bower.json` file.


#### Example Input

##### .autocode/config.yml

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

#### Example Output

##### bower.json

```json
{
	"authors": [
		"Betty Beta <bbeta@example.com>"
	],
	"dependencies": {
		"get-size": "~1.2.2",
		"eventEmitter": "~4.2.11"
	},
	"description": "Physics-like animations for pretty particles",
	"devDependencies": {
		"qunit": "~1.16.0"
	},
	"ignore": [
		"**/.*",
		"node_modules",
		"bower_components",
		"test",
		"tests"
	],
	"keywords": [
		"motion",
		"physics",
		"particles"
	],
	"license": "MIT",
	"main": [
		"js/motion.js",
		"sass/motion.scss"
	],
	"moduleType": [
		"amd",
		"globals",
		"node"
	],
	"name": "blue-leaf",
	"version": "1.2.3"
}
```



### <a name="module-PackageSchematic"></a> PackageSchematic
      
Schema for `bower.json` files.



#### Schema

```yaml
type: object
additionalProperties: false
properties:
  name:
    maxLength: 50
    required: true
    type: string
  description:
    maxLength: 140
    type: string
  version:
    type: string
  main:
    type:
      - string
      - array
    items:
      type: string
  moduleType:
    type:
      - string
      - array
    items:
      type: string
  license:
    type:
      - string
      - array
    items:
      type: string
  ignore:
    type: array
    items:
      type: string
  keywords:
    type: array
    items:
      type: string
  authors:
    type: array
    items:
      type:
        - object
        - string
      properties:
        email:
          type: string
        homepage:
          type: string
        name:
          type: string
  homepage:
    type: string
  dependencies:
    type: object
    properties:
      type: string
  devDependencies:
    type: object
    properties:
      type: string
  resolutions:
    type: object
    properties:
      type: string
  private:
    type: boolean
```



## Help &amp; Support

- [crystal/bower on Crystal Hub](https://hub.crystal.sh/crystal/bower)
- [Report Issues](https://github.com/crystal/bower/issues)
- [Crystal Website](https://crystal.sh)
- [Gitter](https://gitter.im/crystal/autocode)
- [Twitter](https://twitter.com/crystalcodegen)
- [Facebook](https://facebook.com/crystalcodegen)