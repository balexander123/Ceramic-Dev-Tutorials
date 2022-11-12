# Exploring DID Methods

## Run a local ceramic node

### Install Ceramic CLI

We need to install the Ceramic CLI to be able to run a local Ceramic node.

```zsh

% npm i -g @ceramicnetwork/cli

```
### Start A Local Ceramic Node Instance

For local development and testing, we will start a Ceramic node using the ```ceramic``` command:

```zsh

% ceramic daemon --hostname localhost

```

You will see a log of startup messages in the console as ceramic starts up.  Wait until you see a message like this:

```zsh

[2022-11-11T01:41:27.611Z] IMPORTANT: Ceramic API running on localhost:7007'

```

Your local ceramic instance is up and running!

### Install Glaze CLI

Now we will install the new Glaze CLI to execute commands against our locally running ceramic node.

```zsh

npm i -g @glazed/cli

```

### Setup your Admin private key DIDs

In order to interact with the restricted admin APIs on your  Ceramic instance, you will need to create a DID private key.  The DIDs used in this Ceramic walkthru use the Decentralized ID method [did:key](https://w3c-ccg.github.io/did-method-key/#introduction) and is a simple type of identifier for verifiable, decentralized digital identity.

In a separate shell and with the Ceramic daemon running in another shell, execute the ```did:create``` command to create a DID:

```zsh

% glaze did:create
✔ Created DID did:key:z6Mknxv35RDpkX63N9Lzgzk4YRqSeN643L6cBq45XCpKaQvi with seed df2ec2c237540a2f2a50e012169a72e491b1136a9e0e4faaee0e3746c40fe77d

```

Note and keep safe the seed that appears in the ```did:create``` output.  We will need this later to pass to any restricted access Ceramic APIs.

For example, to create a **Tile** with the ```tile:create``` command, we will pass the DID seed using the ```--key``` parameter:

```zsh

% glaze tile:create --content='{ "title": "My first Document" }' --key=df2ec2c237540a2f2a50e012169a72e491b1136a9e0e4faaee0e3746c40fe77d
ℹ Using DID did:key:z6Mknxv35RDpkX63N9Lzgzk4YRqSeN643L6cBq45XCpKaQvi
✔ Created stream kjzl6cwe1jw148ofiinmmhnuc5rd3zbfqt7qsscahfi20kcn9hx9n7c30v5ie3o.
{
  streamID: 'kjzl6cwe1jw148ofiinmmhnuc5rd3zbfqt7qsscahfi20kcn9hx9n7c30v5ie3o',
  content: { title: 'My first Document' }
}

```

### did:inspect  inspect the contents of a DID DataStore

We can inspect the DID to show objects stored in the DataStore

```

% glaze did:inspect --key=df2ec2c237540a2f2a50e012169a72e491b1136a9e0e4faaee0e3746c40fe77d
ℹ Using DID did:key:z6Mknxv35RDpkX63N9Lzgzk4YRqSeN643L6cBq45XCpKaQvi
✔ Index stream loaded

```

#### did:get      get the contents of a record in a DID DataStore

#### did:merge    merge the contents of a record in a DID DataStore

#### did:set      set the contents of a record in a DID DataStore

#### did:sign     create a JSON Web Signature

#### did:verify   verify a JSON Web Signature

For full documentation visit [mkdocs.org](https://www.mkdocs.org).

## Commands

* `mkdocs new [dir-name]` - Create a new project.
* `mkdocs serve` - Start the live-reloading docs server.
* `mkdocs build` - Build the documentation site.
* `mkdocs -h` - Print help message and exit.

## Project layout

    mkdocs.yml    # The configuration file.
    docs/
        index.md  # The documentation homepage.
        ...       # Other markdown pages, images and other files.
