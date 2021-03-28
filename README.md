# Release Notes

This action compiles the commits between the latest release tag and a head ref into release notes. For use with [actions/create-release](https://github.com/actions/create-release).

-   If no release tags exist, only the HEAD commit will be compiled.

## Inputs

### `head-ref`

**Optional** Custom head ref. Default is `HEAD`.

### `format`

**Optional** Release note format. Default is `- {{subject}} by @{{author}}`.

## Outputs

### `release-notes`

Multi-lined release notes e.g.
```
- Do more stuff (#2) by @johnyherangi
- Do stuff (#1) by @johnyherangi
```

## Example usage

```yaml
- uses: johnyherangi/release-notes@master
  id: release_notes
  env:
      GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
- uses: actions/create-release@v1
  env:
      GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
  with:
      tag_name: '1.0.0'
      release_name: My Release
      body: ${{ steps.release_notes.outputs.release-notes }}
```
