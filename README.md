# Setup Binary Ninja GitHub Action

Setup Binary Ninja for unit tests

## Usage

This action is designed to be used in other repositories' workflows. It requires a Binary Ninja archive (7z format) to be present in the `binaryninja/<version>/` directory of this action repository.

```yaml
- name: Setup Binary Ninja
  uses: MCPPhalanx/action-setup-binaryninja@main
  with:
    version: '4.2.6455'  # The version of Binary Ninja to use
    password: ${{ secrets.BINARYNINJA_PASSWORD }}  # Decryption password for the archive
```

## Inputs

| Input | Description | Required | Default |
|-------|-------------|----------|--------|
| `version` | Binary Ninja version to use | Yes | `4.2.6455` |
| `password` | Decryption password for the Binary Ninja archive | Yes | N/A |

## Outputs

| Output | Description |
|--------|-------------|
| `install-path` | Path to the installed Binary Ninja core files (`/opt/binaryninja`) |
| `user-dir` | Path to the Binary Ninja user directory (`~/.binaryninja`) where `license.dat` is placed. The `BN_USER_DIRECTORY` environment variable is also set to this path. |

## Archive Structure

This action expects Binary Ninja archives (`binaryninja.7z`) to be stored in the `binaryninja/<version>/` directory of this action repository. The archive should be password-protected and contain:

- A `binaryninja` directory (this will be extracted to `/opt/binaryninja`)
- A `license.dat` file (this will be extracted to `~/.binaryninja/license.dat`)

Example structure within the `binaryninja.7z` archive:

```
binaryninja/
  # ... Binary Ninja files and folders ...
license.dat
```

And the action repository should have:
```
binaryninja/
  <version>/
    binaryninja.7z
```

The `.gitignore` file is configured to ignore the `.zip` files in these directories.

## License

This project is licensed under the terms specified by Binary Ninja's licensing agreement.