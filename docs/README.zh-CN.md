# GitHub Profile 3D Contrib

![svg](https://raw.githubusercontent.com/Jung217/github-profile-3d-contrib/main/docs/demo/profile-gitblock.svg)

<!-- è¯­è?ä»??é¡ºå?ï¼ˆè‹±è¯­é™¤å¤–ï? -->
[English (en)](../README.md) |
[Deutsch (de)](README.de.md) |
[EspaÃ±ol (es)](README.es.md) |
[FranÃ§ais (fr)](README.fr.md) |
[?¥æœ¬èª?(ja)](README.ja.md) |
[?œêµ­??(ko)](README.ko.md) |
[PortuguÃªs (pt-BR)](README.pt-br.md) |
[PortuguÃªs (pt)](README.pt.md) |
[????ĞºĞ¸Ğ¹ (ru)](README.ru.md) |
ç®€ä½“ä¸­??(zh-CN) |
[ç¹é?ä¸­æ? (zh-TW)](README.zh-TW.md) |

> [!NOTE]
> æ­¤ç¿»è¯‘ç”±?ºå™¨ç¿»è??Ÿæ???
> å®ƒå¯?½å??«é?è¯¯æ?ä¸è‡ª?¶ç?è¡¨è¾¾??
> æ¬¢è?ä¸ºæ”¹è¿›ç¿»è¯‘å??ºè´¡?®ï?

## æ¦‚è¿°

æ­?GitHub Action ä¼šåœ¨?¨ç? 3D ä¸ªäººèµ„æ??¾ç?ä¸Šç???GitHub è´¡çŒ®?¥å???

## å¦‚ä?ä½¿ç”¨ï¼ˆGitHub Actionsï¼? ?ºæœ¬

æ­?GitHub Action ä¼šç??æ‚¨??GitHub ä¸ªäººèµ„æ? 3D è´¡çŒ®?¥å?å¹¶æ?äº¤åˆ°?¨ç?ä»“å???
æ·»å? GitHub Action ?ï?å·¥ä?æµä?æ¯å¤©?ªåŠ¨è¿è?ä¸€æ¬¡ã€?
?¨ä??¯ä»¥?‹åŠ¨è§¦å?å·¥ä?æµã€?

### æ­¥éª¤ 1. ?›å»º?¹æ??„ä¸ªäººè??™ä?åº?

??GitHub ä¸Šå?å»ºä?ä¸ªä??¨ç??¨æˆ·?ç›¸?Œå?ç§°ç?ä»“å???

- ä¾‹å?ï¼Œå??œç”¨?·å?ä¸?`octocat`ï¼Œå??›å»º?ä¸º `octocat/octocat` ?„ä?åº“ã€?
- ?‚è€ƒï?[ç®¡ç?ä¸ªäººèµ„æ??ªè¿°?‡ä»¶](https://docs.github.com/zh/account-and-profile/how-tos/setting-up-and-managing-your-github-profile/customizing-your-profile/managing-your-profile-readme)

?¨æ­¤ä»“å?ä¸­ï??‰ç…§ä»¥ä?æ­¥éª¤?ä???

### æ­¥éª¤ 2. ?›å»ºå·¥ä?æµæ?ä»?

?›å»ºå¦‚ä?å·¥ä?æµæ?ä»¶ã€?

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
> ?¨å¯ä»¥æ›´??GitHub è®¾ç½®ä»¥å??«æ¥?ªç??‰ä?åº“ç?è´¡çŒ®?‚è??´æ”¹æ­¤è®¾ç½®ï?è¯·ç‚¹?»æ??†è´¡?®æ—¥?†å³ä¸Šè???`Contribution settings`ï¼Œæ??¹å‡»å±å??³ä?è§’ç?å¤´å?ï¼Œé€‰æ‹© `Settings` ??`Public profile` ??`Contributions & Activity`ï¼Œå¹¶?¾é€?`Include private contributions on my profile`??
>
> å¦‚æ??¨å??›å??«æ¥?ªç??‰ä?åº“ç?é¢å?æ´»åŠ¨ï¼Œè¯·å°†ä¸ªäººè®¿?®ä»¤?Œæ³¨?Œä¸ºå¯†é’¥ï¼Œå¹¶?¨å·¥ä½œæ??‡ä»¶ä¸­è®¾ç½®ä¸º `GITHUB_TOKEN` ?¯å??˜é??‚ä??¨å¤§å¤šæ•°?…å†µä¸‹ï?é»˜è®¤??`secrets.GITHUB_TOKEN` å·²è¶³å¤Ÿã€?

é»˜è®¤?…å†µä¸‹ï?è®¡å?æ¯å¤©è¿è?ä¸€æ¬¡ã€?
?¨å¯ä»¥æ ¹?®é?è¦æ›´?¹è®¡?’æ—¶?´ã€?

è¿™ä?å°†å·¥ä½œæ?æ·»å??°æ‚¨?„ä?åº“ä¸­??

#### ?¯å??˜é?

ç¤ºä?ä¸­åª?‡å?äº?`GITHUB_TOKEN` ??`USERNAME` ?¯å??˜é?ï¼Œä??¨å¯ä»¥æ?å®šä»¥ä¸‹ç¯å¢ƒå??ï?

- `GITHUB_TOKEN` : ï¼ˆå??€ï¼‰è®¿?®ä»¤??
- `USERNAME` : ï¼ˆå??€ï¼‰ç›®?‡ç”¨?·å?ï¼ˆæ??šè??‚æ•°?‡å?ï¼‰ã€?
- `MAX_REPOS` : ï¼ˆå¯?‰ï??€å¤§ä?åº“æ•°ï¼Œé?è®?100 - ??v0.2.0 èµ?
- `SETTING_JSON` : ï¼ˆå¯?‰ï?è®¾ç½® json ?‡ä»¶è·¯å??‚è¯¦?…è¯·?‚è?ä»“å?ä¸­ç? `sample-settings/*.json` ??`src/type.ts`?? ??v0.6.0 èµ?
- `GITHUB_ENDPOINT` : ï¼ˆå¯?‰ï?Github GraphQL ç«¯ç‚¹?‚ä?å¦‚ï?å¦‚æ??¨å??›åŸºäºå…¬??GitHub Enterprise æ´»åŠ¨?Œä???GitHub.com ?›å»ºè´¡çŒ®?¥å?ï¼Œè¯·è®¾ç½®æ­¤ç¯å¢ƒå??ã€‚ä?å¦‚ï?`https://github.mycompany.com/api/graphql` - ??v0.8.0 èµ?
- `YEAR` : ï¼ˆå¯?‰ï?å¦‚é??Ÿæ?å¾€å¹´æ—¥?†ï?è¯·æ?å®šå¹´ä»½ã€‚æ­¤é¡¹ä¸»è¦ç”¨äºå‘½ä»¤è?è¿è?å·¥å…·?¶æ?å®šã€? ??v0.8.0 èµ?

#### ?³ä? `GITHUB_TOKEN`

ç¤ºä?ä¸­è®¾ç½®ä¸º `GITHUB_TOKEN` ?¯å??˜é???`secrets.GITHUB_TOKEN` ??GitHub ?ªåŠ¨?›å»º?„ç‰¹æ®Šè®¿?®ä»¤?Œã€?

- GitHub ?‡æ¡£: [?¨å·¥ä½œæ?ä¸­ä½¿??GITHUB_TOKEN è¿›è?èº«ä»½éªŒè?](https://docs.github.com/zh/actions/tutorials/authenticate-with-github_token)

å¦‚æ??¨åª?³ä¸º?¬å…±ä»“å??Ÿæ?è´¡çŒ®?¥å?ï¼Œè¯·ä½¿ç”¨æ­¤å€¼ã€?
? é??‹åŠ¨?›å»ºå¯†é’¥??

æ­¤å?ï¼Œå??œæ‚¨å¸Œæ??¨è´¡?®æ—¥?†ä¸­?…å«ç§æ?ä»“å??„æ´»?¨ï?è¯·åœ¨ä¸ªäººèµ„æ?è®¾ç½®??"Public profile" ?¨å???"Profile settings" ä¸­å‹¾??"Include private contributions on my profile"??

å¦‚æ?è¿˜å??›å??«æ¥?ªç??‰ä?åº“ç?é¢å?æ´»åŠ¨ä¿¡æ¯ï¼Œè¯·?›å»º?·æ??‚å??ƒé??„è®¿?®ä»¤?Œã€?
å°†è¯¥è®¿é—®ä»¤ç?æ³¨å?ä¸ºä»»?å?ç§°ç?å¯†é’¥ï¼ˆä?å¦?`MY_PERSONAL_ACCESS_TOKEN`ï¼‰ã€?
ä½†è¯·æ³¨æ?ï¼Œç”¨?·å?å»ºç?å¯†é’¥ä¸èƒ½ä»?`GITHUB_` å¼€å¤´ã€?

- GitHub ?‡æ¡£: [?ºå?](https://docs.github.com/zh/actions/concepts/security/secrets)

å°†è¯¥å¯†é’¥è®¾ç½®ä¸?`GITHUB_TOKEN` ?¯å??˜é??„å€¼ã€?

```diff
          env:
-           GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
+           GITHUB_TOKEN: ${{ secrets.MY_PERSONAL_ACCESS_TOKEN }}
            USERNAME: ${{ github.repository_owner }}
```

#### ?³ä?è®¡å??¶é—´

ç¤ºä?ä¸­è®¾ç½®ä¸º UTC ?¶é—´ 18:00??
è¿™æ˜¯? ä¸ºä½œè€…æœ¬?°æ—¶?´ä¸º?¥æœ¬?ˆå???

```yaml
on:
  schedule: # 03:00 JST == 18:00 UTC
    - cron: "0 18 * * *"
```

?¨å¯ä»¥æ ¹?®é?è¦æ›´?¹ä¸ºä»»æ??¶é—´??
å»ºè®®è®¾ç½®ä¸ºæœ¬?°æ—¶?´ç??ˆå?ï¼ˆçº¦?Œæ™¨ 3 ?¹ï???
ä½†è¯·æ³¨æ?ï¼Œæ—¶?´å?é¡»ä»¥ UTC ?‡å???

### æ­¥éª¤ 3. ?‹åŠ¨è¿è?æ­?GitHub Action

é¦–æ¬¡è¿è??¶ï?è¯·æ??¨è?è¡Œæ­¤å·¥ä?æµã€?

- `Actions` -> `GitHub-Profile-3D-Contrib` -> `Run workflow`

ä¸ªäººèµ„æ??¾ç?ä¼šç??åœ¨ä»¥ä?è·¯å?ï¼?

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

å¦‚æ??¨æ?å®šä? `SETTING_JSON` ?¯å??˜é?ä¸?json ?‡ä»¶ä¸­æœª?…å« `fileName` å±æ€§ï??™ä??Ÿæ?ä»¥ä??¾ç?ï¼?

- `profile-3d-contrib/profile-customize.svg`

?¨å¯ä»¥å?ä¸‹é¢è¿™æ ·??README.md ä¸­ä½¿?¨è?äº›å›¾?‡ã€?

ç¤ºä?ï¼šç»¿?²ç???

![svg](https://raw.githubusercontent.com/Jung217/github-profile-3d-contrib/main/docs/demo/profile-green-animate.svg)

ç¤ºä?ï¼šå­£?‚ç??¬ï??—å??ƒï?

![svg](https://raw.githubusercontent.com/Jung217/github-profile-3d-contrib/main/docs/demo/profile-season-animate.svg)

ç¤ºä?ï¼šå­£?‚ç??¬ï??—å??ƒï?

![svg](https://raw.githubusercontent.com/Jung217/github-profile-3d-contrib/main/docs/demo/profile-south-season-animate.svg)

ç¤ºä?ï¼šå??¯ç???

![svg](https://raw.githubusercontent.com/Jung217/github-profile-3d-contrib/main/docs/demo/profile-night-view.svg)

ç¤ºä?ï¼šå??´ç»¿?²ç???

![svg](https://raw.githubusercontent.com/Jung217/github-profile-3d-contrib/main/docs/demo/profile-night-green.svg)

ç¤ºä?ï¼šå??´å½©?¹ç???

![svg](https://raw.githubusercontent.com/Jung217/github-profile-3d-contrib/main/docs/demo/profile-night-rainbow.svg)

ç¤ºä?ï¼šgit block ?ˆæœ¬

![svg](https://raw.githubusercontent.com/Jung217/github-profile-3d-contrib/main/docs/demo/profile-gitblock.svg)

### æ­¥éª¤ 4. å°†å›¾?‡æ·»? åˆ° README.md

?¨æ‚¨??README ?‡ä»¶ä¸­æ·»? ç??å›¾?‡ç?è·¯å???

ç¤ºä?ï¼?

```md
![](./profile-3d-contrib/profile-green-animate.svg)
```

## å¦‚ä?ä½¿ç”¨ï¼ˆGitHub Actionsï¼? é«˜çº§ç¤ºä?

- [?´å?ä¿¡æ¯è¯·å?è§?EXAMPLES.md](../EXAMPLES.md)

## å¦‚ä?ä½¿ç”¨ï¼ˆæœ¬?°ï?

å°?`GITHUB_TOKEN` ?¯å??˜é?è®¾ç½®ä¸ºæ‚¨?„ä¸ªäººè®¿?®ä»¤?Œã€?

```sh
export GITHUB_TOKEN=XXXXXXXXXXXXXXXXXXXXX
```

?¨æ‚¨??GitHub ?¨æˆ·?æ??®æ??¨æˆ·?æ›¿??`USER_NAME`ï¼Œè?è¡Œä»¥ä¸‹å‘½ä»¤ã€?

```sh
node_modules/.bin/ts-node src/index.ts USER_NAME
```

??

```sh
npm run build
node . USER_NAME
```

## è®¸å¯è¯?

&copy; 2021 SATO Yoshiyuki. ?‡ç”¨ MIT è®¸å¯è¯ã€?
