# LINE MIDリンク生成ツール

このツールは、LINEのMIDを入力して、特定のLINEアカウントのプロフィールポップアップを開くリンクを生成するためのものです。

---

## デモページ
このツールを試すには、以下のリンクを使用してください：  
[LINE MIDリンク生成ツール](https://mqnk0.github.io/getLineMid)

---

## 使い方

### 1. MIDを準備する
LINEのMID（ユーザー識別子）を準備してください。  
MIDはLINEアカウントごとに一意に割り当てられた文字列です。

### MIDの確認方法

1. **Android端末の場合**  
   MIDは、LINEのチャットデータが保存されている以下のディレクトリにあります：
/storage/emulated/0/Android/data/jp.naver.line.android/files/chats
このディレクトリ内に、LINEのチャットに関連するファイルが保存されています。その中に、MID（ユーザーID）を含むファイルが存在することがあります。

2. **ディレクトリにアクセスする方法**  
- **ファイルマネージャーアプリ**を使って、上記のディレクトリにアクセスする。
- または、**PCを接続**して、Android端末内のこのディレクトリにアクセスします。

3. **MIDの見つけ方**  
- ディレクトリ内にあるフォルダ名が「`u`」で始まっている場合、それがMIDです。

---

### 2. MIDを入力
ツールのテキスト入力欄に、対象アカウントのMIDを入力してください。

### 3. リンクを生成
1. **「リンク生成」ボタン**をクリックします。
2. MIDを元に `line://nv/profilePopup/mid=<入力されたMID>` の形式でリンクが生成されます。
3. 青色のリンク「LINEで開く」とともに説明文が表示されます。

### 4. リンクをクリック
生成されたリンクをクリックすると、LINEアプリが起動し、指定したMIDのユーザーのプロフィールポップアップが開きます。

---

## 注意事項
1. **MIDを入力しない場合**：
- ボタンを押してもアラートが表示され、「MIDを入力してください」と警告されます。
- リンクは生成されません。

2. **動作環境**：
- スマートフォンまたはタブレットでLINEアプリがインストールされている必要があります。
- PCブラウザやデスクトップアプリではリンクが正常に動作しない場合があります。

3. **正しいMIDを使用すること**：
- 正確なMIDでないと、リンクが正しく機能しない場合があります。

---

## ソースコード
以下はツールのHTMLソースコードです。

```html
<!DOCTYPE html>
<html lang="ja">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>LINE MIDリンク生成ツール</title>
<style>
 body {
   font-family: 'Noto Sans JP', sans-serif;
   text-align: center;
   margin-top: 50px;
 }
 input, button {
   font-size: 1.2em;
   padding: 10px;
   margin: 5px;
 }
 a {
   display: block;
   margin-top: 10px;
   font-size: 1.2em;
   color: #1a73e8;
   text-decoration: none;
 }
</style>
</head>
<body>
<h1>LINE MIDリンク生成ツール</h1>
<input type="text" id="midInput" placeholder="MIDを入力してください" />
<button onclick="generateLink()">リンク生成</button>
<p id="instructions" style="display: none;">リンクをクリックするとLINEアプリで開きます。</p>
<a id="lineLink" href="#" target="_self" style="display: none;">LINEで開く</a>

<script>
 function generateLink() {
   const midInput = document.getElementById('midInput').value.trim();
   const lineLink = document.getElementById('lineLink');
   const instructions = document.getElementById('instructions');

   if (midInput) {
     const link = `line://nv/profilePopup/mid=${midInput}`;
     lineLink.href = link;
     lineLink.textContent = 'LINEで開く';
     lineLink.style.display = 'block';
     instructions.style.display = 'block';
   } else {
     alert('MIDを入力してください');
     lineLink.style.display = 'none';
     instructions.style.display = 'none';
   }
 }
</script>
</body>
</html>
```

created by hikakinTV
