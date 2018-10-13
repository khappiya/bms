# bms
MMD化手順メモ .Unity3d > .fbx > .ascii > .pmx 
お、俺用なんだからね。ツール作者に感謝 
ウェイト・ボーンはMMDに持っていけるけど、モーフはわからにゃい・・・ 

１．「ツール・プラグイン」 
　・QuickBMS http://aluigi.altervista.org/quickbms.htm 
　・BMS script http://forum.xentax.com/viewtopic.php?f=16&t=13310 
　・Unity Studio https://ci.appveyor.com/project/Perfare/unitystudio/branch/master/artifacts 
　・Noesis http://richwhitehouse.com/index.php?content=inc_projects.php 
　・Noesis to XNALara/XPS exporter plugin http://xnalara.org/viewtopic.php?f=17&t=1139 
　・Blender 2.78c(最新版) https://www.blender.org/download/ 
　・Blender 2.7 XPS Tools http://johnzero7.deviantart.com/journal/Blender-2-7-XPS-Tools-475948475 
　・Blender2pmx http://u7.getuploader.com/Yjo_oi_Neg/ 


２．「備考」 
　　・すべてのファイル・フォルダ名とパスに２バイト文字を使用しない、長すぎるパスも避ける 
　　・BMS script は、メモ帳に直接貼り付けて.txt形式で保存する 
　　・Noesis Plugin の.pyファイルは Noesis\plugins\pythonフォルダに入れるだけで起動時に自動で読み込んでくれる 
　　・キャラクターの頭部の位置はPMXEditor等を使って手動で合わせる必要がある？ 

81 ：名無しさん＠お腹いっぱい。：2017/05/13(土) 22:54:48.80 ID:DLH2t/id.net
３．「手順」 
　「Quickbms」でlz4形式をアンパック 
　　　・Quickbmsを起動、スクリプトファイルを指定、変換対象のファイルを指定(複数選択可)、出力場所・ファイル名を指定します 
　　　・コンソールで「a」をタイプしEnterキーですべて上書き出力 

　「Unity Studio」を起動、メニュー「File > Load file...」から 右下のウィンドウを「Unity Bundle filees(*.*)」に設定しファイルを読み込みます 
　　　・メニュー「Exprt > All 3d Objects」から.fbx出力　(Noesis.exeを指定しておくと後が楽) 
　　　・メニュー「Exprt > All assets」から.pngテクスチャを出力します 
　　　・.fbxでモデル、ボーンがうまく出せない場合は、チェックボックスを利用し「Exprt > Selected 3D objects」で個別に出力します 

　「Noesis」を起動、.fbxをダブルクリックで開く(ちなみに3Dビュアー右下の赤い骨アイコンを左クリックするとボーンがあるか確認できます) 
　　　・メニュー「File > Export」から、 
　　　　　「Main output type」に「.mesh.ascii - XNALara/XPS 0.9.2」を指定します(※間違えやすい箇所) 
　　　　　「Advanced options」に「-flipuv -scale 250」を入力 
　　　　　　　(デフォルトだとモデルサイズが小さすぎるので250倍に拡大してるけど、この数値じゃなくてもいいです) 

　「Blender」を起動(アドオンを導入しておきます) 
　　　・メニュー「File > Import > XNALara/XPS Model(.ascii/.mesh/.xps)」で.asciiファイルを読み込みます 
　　　・メニュー「File > Export > PMX File for MMD(.pmx)」で.pmxファイルで出力します 

　MMDに読み込ませるとクラッシュする場合、PMXEditorで以下を修正します 
　　　・「表示枠」タブの確認。左側の「共通表示枠」は項目は２つ以上必須。足りなければ「+」ボタンで適当に追加します 
　　　・剛体、Jointをすべて削除 
