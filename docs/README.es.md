# GitHub Profile 3D Contrib

![svg](https://raw.githubusercontent.com/Jung217/github-profile-3d-contrib/main/docs/demo/profile-gitblock.svg)

<!-- Orden del código de idioma (excepto inglés) -->
[English (en)](../README.md) |
[Deutsch (de)](README.de.md) |
Español (es) |
[Français (fr)](README.fr.md) |
[?�本�?(ja)](README.ja.md) |
[?�국??(ko)](README.ko.md) |
[Português (pt-BR)](README.pt-br.md) |
[Português (pt)](README.pt.md) |
[????кий (ru)](README.ru.md) |
[简体中??(zh-CN)](README.zh-CN.md) |
[繁�?中�? (zh-TW)](README.zh-TW.md) |

> [!NOTE]
> Esta traducción fue generada parcialmente por un traductor automático.
> Puede contener errores o expresiones poco naturales.
> ¡Las contribuciones para mejorar la traducción son bienvenidas!

## Visión general

Esta acción de GitHub crea un calendario de contribuciones de GitHub en una imagen de perfil 3D.

## Cómo usar (GitHub Actions) - Básico

Esta acción genera el calendario de contribuciones 3D de tu perfil de GitHub y lo agrega a tu repositorio.
Después de agregar la acción, el flujo de trabajo se ejecuta automáticamente una vez al día.
También puedes activar el flujo de trabajo manualmente.

### Paso 1. Crear un repositorio especial de perfil

Crea un repositorio en GitHub con el mismo nombre que tu nombre de usuario.

- Por ejemplo, si tu nombre de usuario es `octocat`, crea un repositorio llamado `octocat/octocat`.
- Consulta: [Administrar el README de tu perfil](https://docs.github.com/es/account-and-profile/how-tos/setting-up-and-managing-your-github-profile/customizing-your-profile/managing-your-profile-readme)

En este repositorio, sigue los pasos a continuación.

### Paso 2. Crear archivo de workflow

Crea un archivo de workflow como el siguiente.

- `.github/workflows/profile-3d.yml`

```yaml:.github/workflows/profile-3d.yml
name: GitHub-Profile-3D-Contrib

on:
  schedule: # 03:00 JST == 18:00 UTC
    - cron: "0 18 * * *"
  workflow_dispatch:

permissions:
  contents: write

jobs:
  build:
    runs-on: ubuntu-latest
    name: generate-github-profile-3d-contrib
    steps:
      - uses: actions/checkout@v5
      - uses: yoshi389111/github-profile-3d-contrib@latest
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
          USERNAME: ${{ github.repository_owner }}
      - name: Commit & Push
        run: |
          git config user.name github-actions
          git config user.email github-actions@github.com
          git add -A .
          if git commit -m "generated"; then
            git push
          fi
```

> [!NOTE]
> Puedes cambiar la configuración de GitHub para incluir contribuciones de repositorios privados. Para cambiar esta configuración, haz clic en `Contribution settings` en la parte superior derecha del calendario de contribuciones estándar, o haz clic en tu icono en la parte superior derecha de la pantalla, selecciona `Settings` ??`Public profile` ??`Contributions & Activity`, y marca `Include private contributions on my profile`.
>
> Si quieres incluir actividades adicionales de repositorios privados, registra un token de acceso personal como secreto y configúralo en la variable de entorno `GITHUB_TOKEN` en el archivo de workflow. Sin embargo, en la mayoría de los casos el valor predeterminado `secrets.GITHUB_TOKEN` es suficiente.

La programación está configurada para ejecutarse una vez al día por defecto.
Puedes cambiar la hora programada como desees.

Esto agregará el workflow a tu repositorio.

#### Variables de entorno

En el ejemplo, solo se especifican `GITHUB_TOKEN` y `USERNAME`, pero puedes usar las siguientes variables de entorno:

- `GITHUB_TOKEN` : (requerido) token de acceso
- `USERNAME` : (requerido) nombre de usuario objetivo (o especificar como argumento).
- `MAX_REPOS` : (opcional) número máximo de repositorios, por defecto 100 - desde ver. 0.2.0
- `SETTING_JSON` : (opcional) ruta del archivo json de configuración. Consulta `sample-settings/*.json` y `src/type.ts` en el repositorio `yoshi389111/github-profile-3d-contrib` para más detalles. - desde ver. 0.6.0
- `GITHUB_ENDPOINT` : (opcional) endpoint de Github GraphQL. Por ejemplo, si quieres crear el calendario de contribuciones basado en la actividad de GitHub Enterprise de tu empresa en vez de GitHub.com, configura esta variable. Ejemplo: `https://github.mycompany.com/api/graphql` - desde ver. 0.8.0
- `YEAR` : (opcional) Para calendarios pasados, especifica el año. Pensado para ejecución desde la línea de comandos. - desde ver. 0.8.0

#### Sobre `GITHUB_TOKEN`

El valor `secrets.GITHUB_TOKEN` en la variable de entorno `GITHUB_TOKEN` es un token especial creado automáticamente por GitHub.

- GitHub Docs: [Uso de GITHUB_TOKEN para la autenticación en flujos de trabajo](https://docs.github.com/es/actions/tutorials/authenticate-with-github_token)

Si solo quieres generar el calendario de contribuciones para repositorios públicos, usa este valor.
No es necesario crear un secreto manualmente.

Si quieres incluir actividad de tus repositorios privados en el calendario de contribuciones, marca "Incluir contribuciones privadas en mi perfil" en la sección "Perfil público" de la configuración de tu perfil.

Además, si quieres incluir información adicional de actividad de repositorios privados, crea un token de acceso con los permisos adecuados.
Registra ese token como secreto con el nombre que desees (por ejemplo, `MY_PERSONAL_ACCESS_TOKEN`).
Ten en cuenta que los secretos creados por el usuario no pueden empezar por `GITHUB_`.

- GitHub Docs: [Secretos](https://docs.github.com/es/actions/concepts/security/secrets)

Configura ese secreto como valor de la variable de entorno `GITHUB_TOKEN`.

```diff
          env:
-           GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
+           GITHUB_TOKEN: ${{ secrets.MY_PERSONAL_ACCESS_TOKEN }}
            USERNAME: ${{ github.repository_owner }}
```

#### Sobre la hora de programación

En el ejemplo, está configurado para ejecutarse a las 18:00 UTC.
Esto es porque se ejecutará a medianoche JST, la hora local del autor.

```yaml
on:
  schedule: # 03:00 JST == 18:00 UTC
    - cron: "0 18 * * *"
```

Puedes cambiarlo a la hora que prefieras.
Se recomienda la medianoche (alrededor de las 3am) de tu hora local.
Recuerda que la hora debe especificarse en UTC.

### Paso 3. Ejecutar manualmente la acción de GitHub

La primera vez, ejecuta este workflow manualmente.

- `Actions` -> `GitHub-Profile-3D-Contrib` -> `Run workflow`

Las imágenes de perfil se generan en las siguientes rutas:

- `profile-3d-contrib/profile-green-animate.svg`
- `profile-3d-contrib/profile-green.svg`
- `profile-3d-contrib/profile-season-animate.svg`
- `profile-3d-contrib/profile-season.svg`
- `profile-3d-contrib/profile-south-season-animate.svg`
- `profile-3d-contrib/profile-south-season.svg`
- `profile-3d-contrib/profile-night-view.svg`
- `profile-3d-contrib/profile-night-green.svg`
- `profile-3d-contrib/profile-night-rainbow.svg`
- `profile-3d-contrib/profile-gitblock.svg`

Si especificas la variable de entorno `SETTING_JSON` sin la propiedad `fileName` en el archivo json, se generará la siguiente imagen:

- `profile-3d-contrib/profile-customize.svg`

Puedes usar estas imágenes en tu README.md como se muestra a continuación.

Ejemplo: versión green

![svg](https://raw.githubusercontent.com/Jung217/github-profile-3d-contrib/main/docs/demo/profile-green-animate.svg)

Ejemplo: versión season (hemisferio norte)

![svg](https://raw.githubusercontent.com/Jung217/github-profile-3d-contrib/main/docs/demo/profile-season-animate.svg)

Ejemplo: versión season (hemisferio sur)

![svg](https://raw.githubusercontent.com/Jung217/github-profile-3d-contrib/main/docs/demo/profile-south-season-animate.svg)

Ejemplo: versión night view

![svg](https://raw.githubusercontent.com/Jung217/github-profile-3d-contrib/main/docs/demo/profile-night-view.svg)

Ejemplo: versión night green

![svg](https://raw.githubusercontent.com/Jung217/github-profile-3d-contrib/main/docs/demo/profile-night-green.svg)

Ejemplo: versión night rainbow

![svg](https://raw.githubusercontent.com/Jung217/github-profile-3d-contrib/main/docs/demo/profile-night-rainbow.svg)

Ejemplo: versión git block

![svg](https://raw.githubusercontent.com/Jung217/github-profile-3d-contrib/main/docs/demo/profile-gitblock.svg)

### Paso 4. Agregar imagen al README.md

Agrega la ruta de la imagen generada en tu archivo README.

Ejemplo:

```md
![](./profile-3d-contrib/profile-green-animate.svg)
```

## Cómo usar (GitHub Actions) - Ejemplos avanzados

- [Más información en EXAMPLES.md](../EXAMPLES.md)

## Cómo usar (local)

Configura la variable de entorno `GITHUB_TOKEN` con tu token de acceso personal.

```sh
export GITHUB_TOKEN=XXXXXXXXXXXXXXXXXXXXX
```

Ejecuta el siguiente comando, reemplazando `USER_NAME` por tu nombre de usuario de GitHub o el nombre de usuario objetivo.

```sh
node_modules/.bin/ts-node src/index.ts USER_NAME
```

o

```sh
npm run build
node . USER_NAME
```

## Licencia

&copy; 2021 SATO Yoshiyuki. Licensed under the MIT License.
