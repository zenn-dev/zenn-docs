## changelog.jsonについて

このJSONファイルの内容が https://zenn.dev/changelog に反映される

### サポートされているプロパティ

```js
{
  "yyyymmdd": number; // required
  "type": 'BugFix' | 'Feature' | 'Improve' | 'Chore'; // required
  "title": string; // required
  "breaking"?: boolean;
  "detailHtml"?: string;
  "detailUrl"?: string;
  "imageUrl"?: string;
  "important"?: boolean;
  "needUpdateCLI"?: boolean;
}
```


