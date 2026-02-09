# GitHub Profile 3D Contrib

![svg](https://raw.githubusercontent.com/Jung217/github-profile-3d-contrib/main/docs/demo/profile-gitblock.svg)

<!-- èªè??†å?ï¼ˆä??«è‹±?‡ï? -->
[English (en)](../README.md) |
[Deutsch (de)](README.de.md) |
[EspaÃ±ol (es)](README.es.md) |
[FranÃ§ais (fr)](README.fr.md) |
[?¥æœ¬èª?(ja)](README.ja.md) |
[?œêµ­??(ko)](README.ko.md) |
[PortuguÃªs (pt-BR)](README.pt-br.md) |
[PortuguÃªs (pt)](README.pt.md) |
[????ĞºĞ¸Ğ¹ (ru)](README.ru.md) |
[ç®€ä½“ä¸­??(zh-CN)](README.zh-CN.md) |
ç¹é?ä¸­æ? (zh-TW) |

> [!NOTE]
> ?¬ç¿»è­¯ç”±æ©Ÿå™¨?ªå??Ÿæ???
> ?¯èƒ½?…å«?¯èª¤?–ä??ªç„¶?„è¡¨?”ã€?
> æ­¡è??”åŠ©?¹é€²ç¿»è­¯ï?

## æ¦‚è¿°

æ­?GitHub Action ?ƒåœ¨ 3D ?‹äººæª”æ??–ç?ä¸Šå»ºç«?GitHub è²¢ç»?¥æ???

## å¦‚ä?ä½¿ç”¨ï¼ˆGitHub Actionsï¼? ?ºæœ¬

æ­?GitHub Action ?ƒç”¢?Ÿæ‚¨??3D è²¢ç»?¥æ?ä¸¦æ?äº¤åˆ°?¨ç??‰åº«??
?°å? Action å¾Œï?å·¥ä?æµç?æ¯å¤©?ƒè‡ª?•åŸ·è¡Œä?æ¬¡ã€?
?¨ä??¯ä»¥?‹å?è§¸ç™¼å·¥ä?æµç???

### æ­¥é? 1. å»ºç??¹æ??‹äººæª”æ??‰åº«

??GitHub ä¸Šå»ºç«‹ä??‹è??¨ç?ä½¿ç”¨?…å?ç¨±ç›¸?Œç??‰åº«??

- ä¾‹å?ï¼Œè‹¥ä½¿ç”¨?…å?ç¨±ç‚º `octocat`ï¼Œå?å»ºç??ç‚º `octocat/octocat` ?„å€‰åº«??
- ?ƒè€ƒï?[Managing your profile README](https://docs.github.com/en/account-and-profile/how-tos/setting-up-and-managing-your-github-profile/customizing-your-profile/managing-your-profile-readme)

?¨æ­¤?‰åº«ä¸­ï?è«‹ä??§ä»¥ä¸‹æ­¥é©Ÿæ?ä½œã€?

### æ­¥é? 2. å»ºç?å·¥ä?æµç?æª”æ?

å»ºç?å¦‚ä??„å·¥ä½œæ?ç¨‹æ?æ¡ˆã€?

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
> ?¨å¯ä»¥è???GitHub è¨­å?ä»¥å??«ç?äººå€‰åº«?„è²¢?»ã€‚è?é»é¸æ¨™æ?è²¢ç»?¥æ??³ä?è§’ç??Œè²¢?»è¨­å®šã€ï??–é??¸å³ä¸Šè??„å€‹äºº?–ç¤ºï¼Œé¸?‡ã€Œè¨­å®šã€â??Œå…¬?‹å€‹äººæª”æ??â??Œè²¢?»è?æ´»å??ï?ä¸¦å‹¾?¸ã€Œåœ¨?‘ç??‹äººæª”æ?ä¸­å??«ç?äººè²¢?»ã€ã€?
>
> ?¥è?é¡å??…å«ç§äºº?‰åº«?„æ´»?•ï?è«‹å??‹äººå­˜å?æ¬Šæ?è¨»å??ºæ?å¯†ï?ä¸¦åœ¨å·¥ä?æµç?æª”æ?ä¸­è¨­å®šç‚º `GITHUB_TOKEN` ?°å?è®Šæ•¸?‚ä?å¤§å??¸æ?æ³ä?ï¼Œé?è¨­ç? `secrets.GITHUB_TOKEN` å·²è¶³å¤ ã€?

?è¨­?’ç??ºæ?å¤©åŸ·è¡Œä?æ¬¡ã€?
?¨å¯ä¾é?æ±‚èª¿?´æ?ç¨‹æ??“ã€?

?™æ?å°‡å·¥ä½œæ?ç¨‹æ–°å¢è‡³?¨ç??‰åº«??

#### ?°å?è®Šæ•¸

ç¯„ä?ä¸­å??‡å?äº?`GITHUB_TOKEN` ??`USERNAME`ï¼Œä??¨å¯?‡å?ä»¥ä??°å?è®Šæ•¸ï¼?

- `GITHUB_TOKEN`ï¼šï?å¿…å¡«ï¼‰å??–æ???
- `USERNAME`ï¼šï?å¿…å¡«ï¼‰ç›®æ¨™ä½¿?¨è€…å?ç¨±ï??–ä»¥?ƒæ•¸?‡å?ï¼‰ã€?
- `MAX_REPOS`ï¼šï??¸å¡«ï¼‰æ?å¤§å€‰åº«?¸ï??è¨­ 100 - ??v0.2.0 èµ?
- `SETTING_JSON`ï¼šï??¸å¡«ï¼‰è¨­å®?json æª”æ?è·¯å??‚è©³è¦?`sample-settings/*.json` ??`src/type.ts`?? ??v0.6.0 èµ?
- `GITHUB_ENDPOINT`ï¼šï??¸å¡«ï¼‰Github GraphQL ç«¯é??‚ä?å¦‚ï??¥è??¹æ??¬å¸ GitHub Enterprise æ´»å?å»ºç?è²¢ç»?¥æ?ï¼Œè?è¨­å?æ­¤ç’°å¢ƒè??¸ã€‚ä?å¦‚ï?`https://github.mycompany.com/api/graphql` - ??v0.8.0 èµ?
- `YEAR`ï¼šï??¸å¡«ï¼‰æ?å®šå¹´ä»½ä»¥?¢ç??å»?„æ—¥?†ã€‚å??å‘½ä»¤å??·è??‚æ?å®šã€? ??v0.8.0 èµ?

#### ?œæ–¼ `GITHUB_TOKEN`

ç¯„ä?ä¸­æ–¼ `GITHUB_TOKEN` ?°å?è®Šæ•¸è¨­å???`secrets.GITHUB_TOKEN` ??GitHub ?ªå?å»ºç??„ç‰¹æ®Šå??–æ??–ã€?

- GitHub ?‡ä»¶ï¼š[Use GITHUB_TOKEN for authentication in workflows](https://docs.github.com/en/actions/tutorials/authenticate-with-github_token)

?¥å??€?¢ç??¬é??‰åº«?„è²¢?»æ—¥?†ï?è«‹ä½¿?¨æ­¤?¼ã€?
?¡é??‹å?å»ºç?æ©Ÿå???

?¥è??¨è²¢?»æ—¥?†ä¸­?…å«ç§äºº?‰åº«æ´»å?ï¼Œè??¨å€‹äººæª”æ?è¨­å??„ã€Œå…¬?‹å€‹äººæª”æ??â??Œè²¢?»è?æ´»å??ä¸­?¾é¸?Œåœ¨?‘ç??‹äººæª”æ?ä¸­å??«ç?äººè²¢?»ã€ã€?

?¥è?é¡å??…å«ç§äºº?‰åº«?„æ´»?•è?è¨Šï?è«‹å»ºç«‹å…·?‰é©?¶æ??ç?å­˜å?æ¬Šæ???
å°‡è©²æ¬Šæ?è¨»å??ºæ?å¯†ï??ç¨±?¯è‡ªè¨‚ï?å¦?`MY_PERSONAL_ACCESS_TOKEN`ï¼‰ã€?
ä½†è?æ³¨æ?ï¼Œä½¿?¨è€…å»ºç«‹ç?æ©Ÿå??ç¨±ä¸å¯ä»?`GITHUB_` ?‹é ­??

- GitHub ?‡ä»¶ï¼š[Secrets](https://docs.github.com/en/actions/concepts/security/secrets)

å°‡è©²æ©Ÿå?è¨­ç‚º `GITHUB_TOKEN` ?°å?è®Šæ•¸?„å€¼ã€?

```diff
          env:
-           GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
+           GITHUB_TOKEN: ${{ secrets.MY_PERSONAL_ACCESS_TOKEN }}
            USERNAME: ${{ github.repository_owner }}
```

#### ?œæ–¼?’ç??‚é?

ç¯„ä?è¨­å???18:00 UTC ?·è???
?™æ˜¯? ç‚ºä½œè€…ç??¬åœ°?‚é???JST ?ˆå???

```yaml
on:
  schedule: # 03:00 JST == 18:00 UTC
    - cron: "0 18 * * *"
```

?¨å¯?ªç”±èª¿æ•´?‚é???
å»ºè­°è¨­ç‚º?¬åœ°?‚é??ˆå?ï¼ˆç??Œæ™¨ 3 é»ï???
ä½†è?æ³¨æ?ï¼Œæ??“é?ä»?UTC ?‡å???

### æ­¥é? 3. ?‹å??·è? GitHub Action

é¦–æ¬¡è«‹æ??•åŸ·è¡Œæ­¤å·¥ä?æµç???

- `Actions` -> `GitHub-Profile-3D-Contrib` -> `Run workflow`

?‹äººæª”æ??–ç?å°‡ç”¢?Ÿæ–¼ä»¥ä?è·¯å?ï¼?

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

?¥æ?å®?`SETTING_JSON` ?°å?è®Šæ•¸ä¸?json æª”æ??ªå« `fileName` å±¬æ€§ï?å°‡ç”¢?Ÿä»¥ä¸‹å??‡ï?

- `profile-3d-contrib/profile-customize.svg`

?¨å¯ä¾ä?ä¾‹æ–¼ README.md ä½¿ç”¨?™ä??–ç???

ç¯„ä?ï¼šç??²ç???

![svg](https://raw.githubusercontent.com/Jung217/github-profile-3d-contrib/main/docs/demo/profile-green-animate.svg)

ç¯„ä?ï¼šå­£ç¯€?ˆï??—å??ƒï?

![svg](https://raw.githubusercontent.com/Jung217/github-profile-3d-contrib/main/docs/demo/profile-season-animate.svg)

ç¯„ä?ï¼šå­£ç¯€?ˆï??—å??ƒï?

![svg](https://raw.githubusercontent.com/Jung217/github-profile-3d-contrib/main/docs/demo/profile-south-season-animate.svg)

ç¯„ä?ï¼šå??¯ç?

![svg](https://raw.githubusercontent.com/Jung217/github-profile-3d-contrib/main/docs/demo/profile-night-view.svg)

ç¯„ä?ï¼šå?ç¶ ç?

![svg](https://raw.githubusercontent.com/Jung217/github-profile-3d-contrib/main/docs/demo/profile-night-green.svg)

ç¯„ä?ï¼šå?å½©è™¹??

![svg](https://raw.githubusercontent.com/Jung217/github-profile-3d-contrib/main/docs/demo/profile-night-rainbow.svg)

ç¯„ä?ï¼šGit Block ??

![svg](https://raw.githubusercontent.com/Jung217/github-profile-3d-contrib/main/docs/demo/profile-gitblock.svg)

### æ­¥é? 4. å°‡å??‡å???README.md

å°‡ç”¢?Ÿç??–ç?è·¯å?? å…¥?¨ç? README æª”æ???

ç¯„ä?ï¼?

```md
![](./profile-3d-contrib/profile-green-animate.svg)
```

## å¦‚ä?ä½¿ç”¨ï¼ˆGitHub Actionsï¼? ?²é?ç¯„ä?

- [?´å?è³‡è?è«‹è? EXAMPLES.md](./EXAMPLES.md)

## å¦‚ä?ä½¿ç”¨ï¼ˆæœ¬?°ç«¯ï¼?

è«‹å? `GITHUB_TOKEN` ?°å?è®Šæ•¸è¨­ç‚º?¨ç??‹äººå­˜å?æ¬Šæ???

```sh
export GITHUB_TOKEN=XXXXXXXXXXXXXXXXXXXXX
```

?·è?ä¸‹å??‡ä»¤ï¼Œå? `USER_NAME` ?¿æ??ºæ‚¨??GitHub ä½¿ç”¨?…å?ç¨±æ??®æ?ä½¿ç”¨?…å?ç¨±ã€?

```sh
node_modules/.bin/ts-node src/index.ts USER_NAME
```

??

```sh
npm run build
node . USER_NAME
```

## ?ˆæ?

&copy; 2021 SATO Yoshiyuki. ?ˆæ??¡ç”¨ MIT License??
