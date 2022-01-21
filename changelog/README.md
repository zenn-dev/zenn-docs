## changelog.jsonについて

このJSONファイルの内容が https://zenn.dev/changelog に反映される

### サポートされているプロパティ

```js
{
  "yyyymmdd": number; // required
  "type": ChangelogType; // required
  "title": string; // required
  "breaking"?: boolean;
  "detailHtml"?: string;
  "detailUrl"?: string;
  "imageUrl"?: string;
  "important"?: boolean;
  "needUpdateCLI"?: boolean;
}
```


