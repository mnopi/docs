# ICONS

## [SVG resize](https://medium.com/@ayumitabinote/how-to-resize-a-svg-image-7829bac8948c)

```xml
<svg big="true" clip-rule="evenodd" fill-rule="evenodd" stroke-linejoin="round" stroke-miterlimit="1.4142" version="1.1"
     width="16px" height="16px" viewBox="0 0 24 24" xml:space="preserve" xmlns="http://www.w3.org/2000/svg">
    <path d="m10 4h-6c-1.11 0-2 .89-2 2v12c0 1.097.903 2 2 2h16c1.097 0 2-.903 2-2v-10c0-1.11-.9-2-2-2h-8l-2-2z"
          fill="#4caf50" fill-rule="nonzero" />
    <path d="m12.282 20.704h10.269v-1.467h-10.269m10.269-6.6016h-2.9341v-4.4011h-4.4011v4.4011h-2.9341l5.1346 5.1346z"
          fill="#c8e6c9" />
</svg>
```

## svg to folder icns and 
`brew install svg2png`
```bash
ICON="download"
ICON="netlify"
SVG="${HOME}/a-file-icon-idea-extend/src/main/resources/iconGenerator/assets/icons/folders/${ICON}.svg"
FOLDER="${1:-$(pwd)}"
PNG="${FOLDER}/icon.png"
mkdir -p "${FOLDER}" && mkdir -p "${FOLDER}/.idea"
echo "${ICON}" > "${FOLDER}/.idea/icon.text"
git add "${FOLDER}/.idea/icon.text"
cp "${SVG}" "${FOLDER}/.idea/icon.svg"
git add "${FOLDER}/.idea/icon.svg"
svg2png --scale=64 "${SVG}" "${PNG}" 
fileicon -q set "${FOLDER}" "${PNG}"
git add "${FOLDER}/Icon?"
git commit -m "${FOLDER}"
```

Other alternative would be with: `sudo -H npm install --global npm install svg-app-icon` 
and `svg-app-icon --destination /tmp/icons < icon.svg`
/netlify.svg
[Icons can also be created with](https://gist.github.com/adriansr/1da9b18a8076b0f8a977a5eea0ae41ef)
