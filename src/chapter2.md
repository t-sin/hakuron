<!-- どうコンピュータ音楽プログラミング言語を研究するか -->

\epigraph{歴史的出来事は、この「人間的コンテクスト」の中で生成し、増殖し、変容し、さらには忘却されもする。端的に言えば「過去は変化する」のであり、逆説的な響きを弱めれば、過去の出来事は新たな「物語行為」に応じて修正され、再編成されるのである。}{『\citefield{Noe1990}{title}』\citep[p11]{Noe1990}}

# 音楽のための道具づくりを研究するとはいったいなんなのか

> *Do the address issues that are most vexing or pressing to musicians? Furthermore, in terms of technology, these contributions seem to be rather unsophisticated.*

> *この論文は音楽家にとってもっとも厄介な、もしくは差し迫った問題を扱っているのでしょうか？さらに言えば、技術的な観点では、本論文の貢献はかなり洗練されていないように見えます。*

これは第6章で扱う、筆者が開発したPLfM、mimiumの設計についての論文を初めてある国際会議に投稿した際ついた査読コメントの一節である。投稿結果はもちろん拒否だった。ただ筆者はこの査読結果に落胆しつつもある程度は仕方ないと諦めをつけていた。第6章で詳細に示すが、mimiumの設計で取り組んだ内容はプログラミング言語理論に対してある程度精通していなければその新規性を伝えることが難しく、かといってプログラミング言語理論について研究する学会の中では、信号処理や音楽の文脈を伝えることも限られたページ数の中では難しい。このとき投稿した国際会議は、投稿を受け付けている時期の問題もあって、音響エンジニアリングに関する研究（例えば信号処理や録音再生技術に関わるもの）が中心的な話題のものだった。もちろん音楽のためのソフトウェア開発はそのトピックの中には含まれてはいたが、PLfMという分野がかなり周縁的な話題である事は投稿の時点で疑いようもなかった。

筆者がやっている事はどうにも技術的に役に立たなさそうで、音楽家にとって興味深いツールになりそうもない、非常に価値の薄い研究をしているのかもしれない。査読コメント読むとどうしてもそうした感情が湧いてくるものの、一方でこのコメントにはどうにも腑に落ちないところもあった[^reviewq]。音楽家にとって**最も厄介な、もしくは差し迫った問題**とはいったい何なのだろうか。そして、音楽家のための道具を作る研究者は、音楽という利害関係や良悪の基準が非常に多様な分野のための道具を作るときにも、常にもっとも差し迫った問題について考えなければならないのだろうか？

[^reviewq]: もっとも、そもそもこの投稿時の査読コメントがこの文章を含めて非常に短く、査読者は一人だけ、技術的コメントはやや的外れなものだったがリバッタル（査読コメントに対する反論を行う機会）が無いなど構造的な問題もあった。

それに加えて、自分の作っているmimiumという言語がまったく的外れで理解不能なことをやっているわけでもないという実感もあった。mimiumという言語の開発は2019年の未踏IT人材発掘・育成事業（以下、未踏事業）という、経済産業省の沿革団体である情報処理推進機構（IPA）が主導する革新的なソフトウェア制作に対して金銭的補助、またコミュニティやメンターからのフィードバックを9ヶ月掛けて受ける支援事業に採択される事で初期の開発が行われた。

未踏事業は2000年度から歴史を持つ、類似する支援事業の中では比較的古くから続いている事業で、その特徴としては採択されるプロジェクトの幅が非常に広く、かつ即効的な実用性のみを必ずしも求めないことがある。例えば筆者が採択された年では、ジャズ演奏の練習を支援するための音源分離技術を利用した「耳コピ」を支援するためのスマートフォン向けアプリケーションのような、すぐにでも実用的に利用できるものもある。かと思えば、秘匿計算（プログラムの入力データを暗号化したまま計算し、暗号化したまま結果を得る技術）のための、実行速度はまだ実用的でないが実際に稼働するプラットフォームの開発のような、セキュリティ技術に関連した非常に基礎的（しかし実現すれば大きなインパクトをもたらし得るもの）な技術を開拓するプロジェクトも含まれる。また事業終了後のアウトプットの形も、論文執筆のようなアカデミックな形だけでなく、事業内で開発したものをもとに起業することも珍しくない。このような応用的な実践と基礎部分の再考という考え方が同居しているコミュニティは後から振り返ってみればかなり珍しいものだ。

筆者のプロジェクトは、採択時のタイトルが「プログラマブルな音楽制作ソフトウェアの開発」となっている通り、その当初のアイデアは音楽のためのプログラミング言語設計とそのソースコードをグラフィカルに編集できるソフトウェアという2つのプロジェクトを並列して行うものになっていた。しかし同事業での過去の採択者や同じ年に採択された人とディスカッションを重ね、プログラミング言語や計算機アーキテクチャ自体の開発に興味を持つ人からのコメントをもらう中で、筆者の興味関心は徐々にその根幹であるプログラミング言語の設計そのものへと少しずつシフトしていった[^mitou]。

[^mitou]: 未踏IT人材発掘・育成事業：2019年度採択プロジェクト概要（松浦PJ）を参照。https://www.ipa.go.jp/jinzai/mitou/2019/gaiyou_tk-1.html 2022年1月31日最終閲覧。また同時期に情報処理学会の音声情報処理研究会にて同様の案についてのポスター発表を行った[@Matsuura2019MUS]。

もちろん、未踏事業のコミュニティにおいても過去に音楽のためのプログラミング言語の開発というテーマの採択はほとんどなく、既に存在しているMaxやPuredataといった既存のツールとの違いの説明や、この言語を作ることが最終的にどういった面白みがあるのかを伝えることは先の学会への論文投稿と同じように課題ではあった。それでも、同事業の成果報告会では、音楽制作ソフトウェアとして実用的に活用するには現実的課題を多く残しつつも、概ね好意的なフィードバックを受けることができた。

あの未踏事業では（その意義を受け入れてもらうのに9ヶ月という長い事業期間があったおかげもあるとは言え）受け入れられ、しかし投稿した論文では差し迫った問題にアプローチしているわけでないという理由で採択されなかった違いとはいったいなんなのだろうか？

本章ではそうした、音楽のための（とくに、コンピューターを用いた）道具を作るということを研究するとはそもそもいったいどういうことなのか、という問いについて考え、本研究を支える研究プログラムそのものの歴史的文脈を構築する。

表現のための道具づくりの研究はとくに、コンピューターの普及が進んで以後ヒューマン・コンピューター・インタラクション（HCI）と呼ばれる、人間が計算機を使う際の相互作用を、主にその境界面：インターフェースを設計することで、その利用方法の拡張を図る学術研究分野で中心的に議論されてきた。

とくに近年ではHCIの研究の方法論の中でも、人工物を作る中での発見を知のあり方とするような、科学と異なる方法論の学術研究としてのデザイン、とくに**デザイン実践を通じた研究（Research through Design：RtD）**と呼ばれる方法論が立ち上がりつつある。

本章の構成としては、まず読者が全体的な研究領域同士の関連性を概観しやすくなるよう、音楽とコンピューティング、プログラミング言語にまたがる研究分野の簡単な見取り図を紹介する。その上で、今日に至るデザインリサーチの歴史的経緯を順を追って説明する。

RtDが立ち上がる中で重要視されてきたのは研究を行う中で自らの考え方や、モノや歴史に対する認識が変化する自己反映性：Reflexivity[^reflex]を研究の過程に織り込むことである。RtDの考え方は日本国内での浸透度合いは未だ不十分だが、国際的にはHCI分野の最大規模の国際会議CHIで20年近く議論が繰り返される中でその歴史的文脈は確立しつつある。しかし、音楽とコンピューティングに跨る分野での研究の方法論の議論の中では、RtDはいまだ十分に着目されてはいない、もしくは単なる問題解決的思考に縮退してしまっている。

本研究は本来のRtDの考え方を一歩推し進め、**ものを作る過程で歴史的視点を再編成する**という立場を取る。とくにメディア論の中で近年立ち上がりつつあるメディア考古学と呼ばれるアプローチや、ダニエラ・K・ロスナーの批判的奇譚づくり（Critical Fabulation）[@Rosner2018]という考え方や、筆者自身のこれまでの作品制作をもとに、PLfMの設計そのものを研究成果とだけするのではなく、その過程で変化した視点をもとに改めて歴史を記述することで学術的な知の貢献とするという考え方をする。

[^reflex]: Reflexivityは再帰性、反射性、反照性、反省性、（原因と結果の）相互参照性など様々な用語で訳される言葉である。本稿ではプログラミング言語理論における再帰（Recursion）との不要な混同を避けるため（実際には広い意味で確かに共通している概念ではあるのだが）、自己反映性という用語を用いる。この語はプログラミング言語において、言語自体の意味論を自己拡張できる、もしくはその言語自体が処理系に機能変更を命令できるような機能：リフレクション（Reflection）の訳として使われるものだ。社会学におけるReflexivityの意味としてはプログラミング言語における再帰よりもこちらの方が類似しているという考えからこの訳を用いる。

# 隣接する学術領域 {#sec:researchfield}

![音楽とコンピューティングに関わる研究領域の見取り図。](img/musiccomputing.pdf){#fig:musiccomputing width=100%}

まず、音楽のためのコンピューターを用いた道具づくりや、本研究で行う音楽のためのプログラミング言語（Programming Language for Music:PLfM）の研究を取り巻く研究領域について概観しよう。代表的な研究領域の重なりを[@fig:musiccomputing]に示した。

上側の大きな囲み：**Computer Science（コンピューター科学）**が、計算機についての研究全般を表す領域である。この図に表されていないがコンピューター科学に含まれる領域としては例えばセキュリティやネットワークに関する研究などが挙げられるだろう。**Human-Computer Interaction（HCI）**と呼ばれる分野は、根本的には数値計算を行うだけのコンピューターという機械を、人間の生活を補助したり創造性の支援を行うなど様々な関わり方をデザインすることを目的とした分野だと言えるだろう。今日では当たり前となっているGUIのようなマウスやキーボードの入力をもとに、演算結果として文字や画像などがディスプレイに即時表示されるインターフェースも、それ以前のパンチカードやテキスト主体の入力方式しか存在しなかった時代を経て、1970年代ごろからのコンピューターの道具としての利用法の拡張を試みてきた結果として確立されてきたものである。

またHCI分野から派生した音楽に関する研究領域として、**New Interfaces for Musical Expression：NIME（音楽表現のための新しいインタフェース）**[^nime]が挙げられる。NIMEは2001年に、HCI分野における世界最大規模の国際会議、CHIの中でのワークショップのひとつとして始まった。現在は独立した国際会議として、単なる研究発表やワークショップのみならず、自作のシステムを用いて行う演奏を中心としたコンサートや、インスタレーション作品展示などが同時に行われている。

[^nime]: https://www.nime.org/ 2022年1月24日最終閲覧。

音楽のためのプログラミング言語はNIMEよりも、**Computer Music（コンピューター音楽）**の分野で長く研究されてきた。これは第4章で詳しく触れるが、今日の音楽のためのプログラミング環境の祖先にあたるものの研究は、1950年代というコンピューター黎明期における、コンピューターを用いて音楽を作ること自体に新規性があった時代の流れを引き継いだものと位置付けられる。そのため、この分野における代表的な国際会議International Computer Music Conference（ICMC）や、Sound and Music Computing（SMC）Conference[^smc]、またMIT Pressが発行する学術誌Computer Music Journal（CMJ）[^cmj]における議論は、その制作環境そのものよりも作られた作品についての議論が中心であると言える。

[^smc]: https://smcnetwork.org/ 2022年1月24日最終閲覧。
[^cmj]: http://www.computermusicjournal.org/ 2022年1月24日最終閲覧。


また**Programming Language（プログラミング言語）**の研究は、大きく分けて実用的に用いる際の課題解決に主眼をおいたものと、言語を抽象的に形式化する理論に寄ったものとがある。前者は音楽に限らないライブプログラミング（実行しながらプログラムを書き換え続ける手法）の研究や、プログラミング体験（Programming Experience：PX）の改善に主眼をおいたものなどがあり、こうした領域はNIMEと同様にHCIの領域と重なってくる。

後者のような理論寄りでありながら、音楽への活用を議論する領域としては、ACM SIGPLAN(Association for Computing Machinary Special Interest Group of Programming Language)の中の、関数型プログラミングと呼ばれる研究領域についての会議ICFP（International Conference of Functional Programming）の、さらにその中で開催されているワークショップ、FARM（Function, Art, Music, Modeling and Design）[^farm]が挙げられる。FARMでは信号処理を対象とした言語や、Haskellなど汎用の関数型言語を用いて実装された音楽のためのライブラリ、作品についての研究がなされている。

[^farm]: https://functional-art.org/ 2022年1月24日最終閲覧。

また**Signal Processing（信号処理）**も音楽とコンピューティングにおいて重要な研究分野だ。信号処理という分野自体はコンピューター登場以前から、音楽に限らない通信分野で電気などのあらゆる種類の信号の伝達についての研究が長く行われてきた。音楽においては電気信号として空気の振動である音声を表現することが一般的になって以降、任意の周波数（≒音の高さ）の信号を抽出するフィルターを電子回路を用いて作るための理論をはじめとして様々な研究がなされている。電子計算機の普及以降は、Digital Signal Processing：DSP（デジタル信号処理）として、電気信号に変わり離散化/量子化を通して任意の数値の列として（音声などの）信号を表現、加工することで、電気回路だけでは難しかった周波数領域での処理（スペクトラルプロセッシング）などが可能になるなどその応用範囲が広がっている。とくに音楽に関わる信号処理の研究が中心の国際会議としてはDAFx[^dafx]のような会議が挙げられる。

[^dafx]: https://www.dafx.de/ 2022年1月24日最終閲覧。

また既に第1章で紹介したように、音圧信号に限らないより高次の音楽に関わるデータの分析や、それをもとにした再合成などを研究する**Music Information Retrieval:MIR（音楽情報検索）**と呼ばれる領域が、国際会議ISMIR[^ismir]などを代表として存在する。MIRでは音声解析と合成（例えば、2chステレオの音源から個別の楽器音を抜き出すような音源分離、テキスト入力を基に音声を合成するText-to-Speechなど）のような研究が行われており、近年では機械学習を用いるアプローチの存在感が増している。もちろん機械学習のような手法はNIMEやICMCにおいても積極的に用いられるようになってきてはいる。ただ、本研究にとって確認しておくべき事項としては、MIRのような分野では用いられる中心的なツールはMATLABやPython、Juliaなどより自然科学分野における分析に向いたプログラミング言語上で構築されたライブラリが主であり、MaxやSuperColliderのようなリアルタイムインタラクションを重視したPLfMが使われることはあまり多くないということだろう[^plfminjapan]。

[^ismir]: https://ismir.net 2022年1月24日最終閲覧。

[^plfminjapan]: なお、日本国内における音楽のためのプログラミング環境を議論するための場としては、情報処理学会（IPSJ）の音楽情報科学研究会（SIGMUS）などが考えられるが、近年では機械学習などを用いた相対的に高レイヤーでの音声情報処理が議論の中心となっている。SIGMUSからより音楽表現に関する議論に重きをおく形で独立した先端芸術音楽創作学会では[@Nishino2014]などの数少ない発表を除き、プログラミング環境自体の構築のような研究はほとんど無い。プログラミング言語研究においては、PXの概念自体の提唱者である、産業技術総合研究所の加藤が立ち上げたSIGPXという勉強会において表現の支援ツールを含めた議論が行われている（筆者も第8回にて第4、5章の議論のベースとなる発表を行なった）。https://sigpx.org/ 2022年1月24日最終閲覧。

本研究で議論しようとしている音楽のためのプログラミング言語（Programming Language for Music：PLfM）という枠組みは筆者が独自に定義するものだ。この語が意味するところは文字通りの意味合いではあるのだが、ここでは特に、Computer Musicの領域に留まらない、より広い意味での音楽のために使われるプログラミング言語に関する研究という意味合いが強調する意味で新しい語を導入している（第4章冒頭を参照）。

# デザインリサーチの変遷——デザインサイエンス、デザイン思考、RtD

![デザインリサーチの歴史の見取り図。](img/design_history.pdf){#fig:designhistory width=100%}

それでは、こうした学問的付置はどのような歴史的経緯で成立してきたのだろうか。本稿ではその成立過程をデザイン学の歴史的変遷を中心にした視点で追いかける。[@fig:designhistory]はその大まかな見取り図と運動に影響を与えた代表的文献を時間軸上に配置したものである。

学問としてのデザインの歴史は大きく分けて以下の3段階の潮流に分けられ、現在もそれぞれの方法論が同居して存在している状況がある。

1. デザイン・サイエンス：科学的、統一的手法による良い人工物の創出の方法論の確立
1. デザイン思考：共感–問題定義–アイデア創出–プロトタイピング–テストの繰り返し
1. Research through Design（RtD）：統一的手法、客観主義、問題解決主義の否定、作る過程での問題発見

ゲイバーがこのような、統一的で定まった学問プログラムが存在していないデザインという領域を**パラダイム成立以前（Pre-Paradigmatic）の研究**と表現しているように[@Gaver2012]、デザイン学の歴史認識や、デザイン学という学問はそもそもどういった方法論の上で研究されているのかの認識は研究者ごとに大きく異なる。この方法論の不明瞭さは音楽とコンピューティングが交差する研究領域においても同様に存在している。[@fig:musiccomputing]の付置でいえば、おおむね下側に行くほど客観主義的/問題解決主義的傾向に寄っていく傾向がある。音楽や表現のための道具作りの研究を行うにあたっては、本章冒頭で引用した査読コメントのような問題解決主義的研究プログラムをそもそも前提としているという齟齬の発生は珍しくない。しかしデザインの歴史の中では、ユーザーに対して決定的な解を提供したり、研究を始める前から問題がはっきりとわかっているような考え方の限界が繰り返し指摘されてきた。一見して無関係に思える工学的な研究に関しても、そもそもどのようにして技術的な問題というものが立ち上がるのか、また誰のために、なぜ問題を解決するのかという思索的な問いは常につきまとっている。これは本研究のような表現に関わる工学的研究という領域において比較的わかりやすい形で表出する問いではあるが、根本的にはどんな種類の工学的研究にも関わってくる問題である。

## デザインの科学化と科学の社会構築

デザインという人工物（プロダクトやシステム）の創出行為を、科学的手法を応用し誰もが普遍的な手段で良いものを作れる方法論として定式化しようとする運動は1960年代ごろに始まっている。

デザイン研究者の水野大二郎は今日までの「デザインリサーチ」の源泉としてデザインサイエンスと呼ばれる1960年代の動向を取り上げ、その要因となる社会的背景として、「欧米社会が豊かになるのに併せてデザインされる対象の規模や機能が拡張、複雑化したと同時に、生産の合理化・効率化が求められた時期」であり、「芸術家的あるいは職人的な経験と勘に基づくデザインメソッド（デザインの方法論）を客観的に学術研究の対象とし、デザインを精緻に理解することが求められた」からだとする[@Mizuno2014]。デザイン・サイエンスの潮流に大きな影響を与えたのが心理学・政治学など人間の意思決定に関する研究者であるハーバート・サイモンによる1969年初版の『The Sciences of the Artificial』[^artificial]である。同書でサイモンは、経済学や認知心理学における当時の最新の知見を取り入れ、世界をシステムとして捉える見方を人工物の創出一般に適用することを試みた。そこには電子計算機がそもそも求められた理由でもある、シミュレーションという行為を通じて我々が世界について知ることができるという意味での、自然環境との境界面：インターフェースとしての人工物の存在意義が示されていた[@Simon1999]。

[^artificial]: 直訳すると『人工物の科学』、邦題は『システムの科学』。

実際1960年代以降にはデザインに限らず建築や芸術作品を作るにあたって科学的なアプローチを用いるものたちによって、言うなればアートやデザインの科学化とも言える現象が起きていた。たとえばデザインサイエンスという言葉を広めた建築家のバックミンスター・フラーや、1968年に行われた、テクノロジーを用いた芸術作品に関する初めての大きな展覧会であるCybernetic Serendipity展、1970年大阪万博におけるE.A.Tが主導したペプシ館の展示のような事象が並べられる。デザインサイエンスやこうしたアート&テクノロジーが1960年代に発展した背景には、ノーバート・ウィーナーやロス・アシュビーのような学者らによって立ち上がったサイバネティクスや、フォン・ベルタランフィの一般システム理論のような、人間と機械の相互制御をフィードバック・システムを中心にして理解しようと試みた学問の隆盛が、そしてそのさらに背景には冷戦による科学技術への国家的投資の過熱があった。今日の人工知能研究のはしりでもあるサイバネティクスの思想は、機械の自動制御にとどまらず、生命の構造をモデル化し、さらには経済や社会までもを大きいひとつの制御可能なシステムと捉えようという形で拡大してきた。

この「あらゆるものの科学（Science of Everything）」は奇妙なことに社会を安定して管理するための手段として国家や軍事産業のテクノクラートたちに受け入れられつつも、同時にフィードバックコントロールを非中央集権的な制御と自己管理と捉えた、ヒッピームーブメントのような左派イデオロギーにも受け入れられたことが知られており[@Bernes2017]デザインやアートといった分野に限らず、経済学や社会計画といった分野にも大きな影響を与えた[^cybernetics]。サイモンの、「現在の状態をより好ましいものに変える」行為としてのデザインという考え方は、現在までRtDの文脈を含めてデザインリサーチの論文で多数引用される考え方になっている[^preferred]。しかしこの言い回しもサイバネティクスに特有の、世界をフィードバックシステムとしてモデル化し、その出力から目標との差分＝エラーを少しづつ増分的に減らしていくことで理想状態へと近づけていくという考え方が色濃く現れたものである。

[^cybernetics]: [@Rid2016]も参照。例えば右派的なものであればチリで1970年代に試みられた国家管理システムCybersynについてのメディナの研究をみよ[@Medina2006]（[@Myers2015]も参照）。左派的なものとしては、Apple創業者のスティーブ・ジョブズにも大きく影響を与えたスチュアート・ブランドによる『全地球カタログ』の第1号の巻頭にウィーナーの書籍が引用されていることがよく知られる。[@Spectator2021]などを参照。

[^preferred]: [@Simon1999,p133]。Research through Designの文脈においてこの考え方を強調している文献としては[@Zimmerman2010]がある。

しかしその一方、同時期に科学論の分野では、自然科学という分野を絶対的真理の探求の営為としてではなく、社会的関係の中に成立する学問として捉える動きが発生している。デザイン学は**パラダイム**成立以前の学問だというゲイバーの主張はすでに引用したが、このパラダイムという語は1962年のトーマス・クーンが『科学革命の構造』の中で、科学者や研究者の中でのある時期の共通した世界認識といった意味合いで導入された語だ[@Kuhn1971]。科学はそれまでポパーが主張してきたように反証可能（Falsifiable）な命題にのみよって示され、そうでないものは疑似科学にしかなり得ないと説明されてきたが、野家の説明を借りればパラダイム論では「理論は事実によってではなく、競合する別の理論によって打ち倒される」[@Noe1981,p69]とされる。その時代で支配的だったパラダイムの中では説明、解決できない問題が出てきたときに全く別の理論体系を採用しなくてはならないときに科学革命＝パラダイム・シフトが発生するのである[^paradigmshift]。科学論としては、例えばデヴィッド・ブルアの『数学の社会学』に代表されるような、自然科学という分野を絶対的真理の探求の営為としてではなく、それすらも科学者というある特定の社会集団の営みとして社会学的に分析でききると捉える**社会構築主義**という立場に大きく影響を与えた[@Fukushima2021,p20]。

[^paradigmshift]: 今日ではパラダイム・シフトという語は、これまで常識とされてきた認識が覆されてしまうような状況全般を指すように拡大した意味で用いられることが多い。

つまり、1960〜70年代はデザインや芸術に科学的手法が取り入れられる一方で、同時にいわば**科学の人文知化**とも言える運動も並行していた。それゆえ、デザイン・サイエンスの運動もこうした科学論の議論を取り入れながら、あらゆる問題をワンストップで解決できるようなシステムの構築を目指す普遍主義（Universalism）とも言えるものが徐々に否定されるようになって来た。

## 意地悪な問題、自己反映性、デザイン思考 {#sec:expectation}

あらゆるもののシステム化というデザイン・サイエンス的思想を支えた考え方の限界は、1973年のデザインの科学的研究者であるリッテルと都市計画研究者であるウェバーによって**意地悪な問題（Wicked Problems）**として提起され[@Rittel1973]、1992年にブキャナンはこれをデザイン学の統一的メソッドづくりの限界の指摘に用いた[@Buchanan1992]。

意地悪な問題は今日のスペキュラティブ・デザインやクリティカル・デザインのような複雑な社会問題に対処することを目指したデザイン運動の議論で必ず現れるほど重要なキーワードのひとつとなっている。リッテルが挙げた意地悪な問題の特徴は以下のようなものである。

1. 決定的な定義と解が存在しない
1. 停止するためのルールが存在しない
1. 解は真か偽ではなく良か悪でしかない
1. 解を得るための即時的に、完璧な結果が得られる実験はありえない
1. 全ての問題に対してトライアンドエラーの機会がない（やればやるほど困難な問題ばかりが残っていく）
1. 解決策や許容される策を網羅的に記述できない
1. 全ての意地悪な問題は本質的にユニークである
1. 全ての問題は他の問題の前兆である
1. 問題の解釈と説明次第で解決策が変わってしまう
1. 意地悪な問題に取り組むものは解決案に責任を負う事になる

意地悪な問題はこの10カ条の形そのままで紹介されることが多いが、その本質は問題設定と解決のプロセスにおける**自己反映性を無視した合理化の限界**という点で共通していることはあまり強調されていない。

意地悪な問題が提起された論文のタイトルは『計画の一般理論におけるジレンマ』というサイバネティクスの残滓が見て取れるタイトルで、政策決定などを科学的根拠と手法に基づいてシステマチックに行うことの限界を示したものだった。リッテルはこの「意地悪な問題」の原点に、合理性（Rationality）に深く根差したパラドックスを挙げる[@Rittel1982]。リッテルのいう合理性とは行動する前にその結果を予測することであり、これには4種類の矛盾が存在するという。

まず1つ目には、（例えば政策決定などで）行動、つまり時間や金銭の投入を実際に開始する前に、その行動が引き起こす価値を最大化するために結果を予測する必要がある。が、その結果の予測のためには何らかの根拠を揃えるための研究活動が必要になる。しかしこの研究活動自体にも時間と金銭を投入しなくてはならないのでその価値の最大化のための基礎研究が…という無限後退が存在する。

2つ目には、例えばある上司が合理的に仕事をこなそうとしている部下を管理する時、部下が実際に行動しはじめた後に上司がそれを何らかの要求で介入して中止することは、部下にとってはどんな理由であれ自分の決定と異なる外的要因による遮断であり非合理的なものとなってしまうということだ。

3つ目は、合理化を進めるほどにある行動のもとに何かが生まれるという予測をするということは、ある種はじめから全ての結末が決まってしまっていることを意味し、行動するためのモチベーションをなくしてしまうという矛盾だ[^rational]。

[^rational]: リッテルはこの矛盾について**合理的に考えたら我々は将来的にみんな死んでいるのだから我々が今何をどうしようが関係のないことだろう**という冗談めいた説明をしている。

4つ目は、モデルがそのモデル自身の未来を自己参照して記述されなければならないという矛盾だ。合理性のための予測は、サイバネティクス的発想で言えば、世界をなるべく現実と同じように振る舞うモデルを構築し、シミュレーションするという説明ができる。しかしこのモデルによって生み出した結果が後の世界の構築に影響を与えるのであれば、そのモデルは世界から生まれたものでもあり、世界を生み出すものであることになってしまうのだ。

この4つの説明を読んだ上で改めて意地悪な問題の10カ条を読み直してみる。意地悪な問題の説明としては、環境や経済、政治問題における説明のように、関連し合う問題が複雑に絡み合っている、複数のステークホルダーごとに価値観が異なるからという理由がよく挙げられる。だがこれらの意味合いは、間違ってはないものの、あくまで結果的な説明でしかないことがわかる。むしろ意地悪な問題の本質とは、ある問題のフレーム設定をする事によって、そのフレーム設定自体が社会に影響を及ぼしてしまい別の問題を発生させたり、問題を記述する事で記述されなかった問題に後々向き合うことが大変になったりするという因果結合の方に重きが置かれていたと理解する方がより正確である。

とはいえこの合理的未来予測における矛盾は確かにあり得そうな一方で、今日わたしたちが歴史を振り返った時には、科学技術が一見線形的に安定して発展してきたように見える事象も確かに存在しており、直感と異なるのをどう説明できるだろうか。たとえば、ムーアの法則という、ICチップに集積されるトランジスタの密度が時間と共に指数関数的に増加することを予測したもの[@Moore1965]は有名な例である。トランジスタの集積密度を上げるための技術的工夫には必ず質的なブレイクスルーが必要であり、そのための技術開発という不確定性を含むはずだが、現実にはかなりの精度で予測の通りの集積密度の発展が成されてきたという事実がある。

この奇妙さについて科学社会技術論の文脈でなされた説明がある。ハロ・ヴァン・レンテらが「科学技術における『期待』の社会学」と銘打った研究の中では、ムーアの法則のような未来予測は結果の予測というよりもむしろ、産業を発展させるための投資をブーストさせるような「期待」を自ら引き起こすことで、産業界などの動向を決定づけるための要因として自己参照的に働くものだとされる。結果的に技術者たちがその期待に応えることによって予測通りの形に落ち着いているように見えている、と解釈するのである[@Yamaguchi2019,p7]。ブラウンやレンテらはこの自己反映的なプロセスを[@fig:brown]の様に入れ子状の過程として説明している[@Brown2003]。

![ブラウンらによる、技術発展における約束と要求の推移過程を示した図。[@Brown2003]をもとに筆者が作成。](img/brown.pdf){width=100% #fig:brown}

何らかの技術的要素が社会的利益を生みそうだという兆候がまずある未来予測（≒ムーアの法則）を生み、その予測をもとに科学技術の進むべき方向性が決定され、一度それが可能な研究となった場合、その研究分野の開発は研究者たちへ「権限が委任(mandate)」される。このとき科学者にとっては安定して研究開発に臨む保護された領域が作られると同時に、その目標の達成に責任（≒ムーアの法則に追いつくこと）を負うことになる。そして実際の実現のためにはこのプロセスがより小規模な可能性と兆候、未来予測に基づいて再起的に発生していくというモデルだ。このネストした循環というのは、たとえばレイ・カーツワイルのシンギュラリティ論[@Kurzweil2007]の様な、典型的技術決定論者の未来予測という大きなループの根拠にムーアの法則が用いられる状況をよく説明している。

リッテルの意地悪な問題の提起とは、こうした期待の社会学の視点では次のように説明し直せる。これまで客観的かつ合理的な予測のもとに発展してきた科学技術とは、本来あり得ないはずの自己参照的未来予測を成立させているように装っているだけであり、実のところは、未来の進むべき方向性を、自らの主体的意図（例えばムーアというICチップを生産する側の人間が自らへの投資を煽ること）という色を薄めつつ浸透させている状況のことだったのだ。意地悪な問題とはつまるところ、サイバネティクス的なフィードバックによる自己調整的社会という虚像のもとシステマチックな思考を推し進めた結果、では結局誰がどう、どこへ社会を進めるべきなのかという議論が欠如していることを自ら露呈させたとも言える。

リッテルの問題提起はデザインの科学的方法による実証主義的、統一的方法での画一化の限界を示し、それが1970年代から1980年代におけるいわゆる「デザイン思考」の文脈における、過度な科学的アプローチに陥らないための方策として、プロトタイピング、実験、思考の繰り返しによる問題発見と問題解決の同時遂行を目指すようなアプローチを生んできた。またここにはドナルド・ショーンの『省察的実践（Reflective Practice）』も、教育分野を中心にして大きな影響を与えた[@Schon2007]。ショーンは自分で実際に手を動かしながら考える（Reflection–in–action）こと、実践の過程で自らが変化する自己反映性の重要さを説き、サイバネティクスにおける自動制御のような身体性の欠如を批判した。

しかしこうしたデザイン思考は、1960年代のデザインサイエンスにおける客観主義を否定はしたものの、今日デザイナーのイメージをアイデアを書いた付箋をホワイトボードに貼ってディスカッションしている人たちに固定してしまったように、あらゆる問題の種類に対して作る（もしくはアイデアを出す）-反省という反復の枠組みだけを与える普遍主義に依然留まってしまっている。

ブキャナンによる意地悪な問題のデザイン思考プロセスにおける紹介はサイモンのようなデザインの科学化に対するアンチテーゼでもあると同時に、デザイン思考がそのプロセスによって問題を確定させる（Determinate）方向に働いているが、そもそもリッテルらが提起した意地悪な問題とは、根本的に確定できない（Indeterminate）ことだったのを強調している。結局人文学的アプローチであったとしても、大枠がプロトタイピング、実験、思考の繰り返しという一般化されたフィードバックでは西門と同じ穴の狢であり意地悪な問題には対応できないということだ。ブキャナンはこれを、確定（Determinate）にはできない主題であっても特殊（Particular）化は可能であり、デザイナーは、クライアントがまだ準主題（Quasi-subject matter）である状態のものを特殊化する事によってエンジニアなどが解決可能な問題にスライドできるという提言をしたのだ。

こうした流れのもと1990年代以降に、**デザイン実践を通じた研究（Research through Design：RtD）**と呼ばれる研究領域が主にデザイン・サイエンス的アプローチの行きづまり（と、並行して起きていたデザイン思考の一般的方法論化）を突破するべく、デザインを「不明瞭かつ個別固有の社会・技術的問題を対象とする臨床的、生成的研究」[@Mizuno2017]と位置付けるような運動として現れてきた[^designresearch]。RtDには、問題を研究する過程で発見すること、必ずしも役に立つものだけを作るわけではないこと、問題解決だけを目的としないこと、社会そのものの変化を視野に入れること、ユーザーではなく参加者/共同製作者への転換、といった様々な特徴が挙げられる。こうした特徴は一見して多岐に渡っており統一性がないようにも思えるが、リッテルの意地悪な問題への動機をもとに考えれば、すべて*どこへ向かうべきか*という社会の中におけるデザイナーの主体性と政治性への自覚という1本の軸から派生したものとして捉えることができる。

[^designresearch]: なおこのような研究として科学と異なる学問プログラムとしての「デザイン」は単にデザインリサーチ（Design Research）と呼称されることもあり、それはマルパスのような丁寧な定義を借りれば「製品やサービスの開発における、多様で複雑な問題の解決策を導くためのデザインプロセスを主に研究する学術領域」[@Marpus2019,p10]ということになる。しかし水野が「日本の産業界においてはデザインリサーチ（＝デザイン研究）という言葉が『新規製品またはサービス開発のために文化人類学を応用した一連のユーザ調査とアイデア創出法』と限定的に理解されている」 と指摘していることに注意して、本項ではRtDという用語を一貫して用いる。

## Design into/through/for Art and Design

Research through Designという言葉が作られるきっかけとなったのはイギリスのロイヤル・カレッジ・オブ・アート（RCA）のクリストファー・フレイリングが1993年に提示した『Research in Art and Design』[@Frayling1993]における以下の3分類である[^mizunotrans]。

- Research **into** art and design （アートやデザインに関する研究）：歴史研究/美学研究/デザインやアートの諸理論に関する研究[^ofandinto]
- Research **through** art and design （アートやデザインを通じた研究）：材料研究/制作実践（を通じたコミュニケーション）/アクションリサーチ
- Research **for** art and design （アートやデザインのための研究）：制作実践のための学び

[^ofandinto]: intoの代わりにofやaboutと置き換えられることもある。

[^mizunotrans]: 訳出は水野らによる以下の資料を参考にした。 https://issuu.com/tacticaldesign/docs/generaloverview/8 (2021/11/23閲覧)

ここでのフレイリングがデザインだけでなくアートという用語も使った分類を提示していた理由に関しては、プログラミング言語を作ることを芸術実践のひとつに捉えようとしている筆者の問題意識とも共通点があるので触れておこう。フレイリングがこの分類を提示した背景はアーティスト、デザイナー、科学者という職業のパブリックイメージとその実際の行為の解離、及びリサーチという行為自体が（たとえ大学にいたとしても）制度化、形骸化されゆくことへの危惧があった。

フレイリングは映画の中でのアーティストや科学者の描かれ方を例に挙げる。アーティスト（ゴッホ）は未だに無からの創造を天才的感性を以って行うように、科学者（フランケンシュタイン博士）は突然のひらめきに導かれる合理的で完璧な理論を持つ人間のように（時には合理化が行きすぎて狂ったマッドサイエンティストとして）描かれるステレオタイプが残っていることを説明する（これは2022年においても未だ根強いものだろう）。しかし既に説明したように、1960〜1980年にはデザインサイエンスやアート&テクノロジーのように、アーティストやデザイナーも作品やプロダクトを作るにあたって科学的知識やテクノロジーを活用していた。同時に科学者側も社会構築主義的科学論で分析されてきたように、直感や身体化された経験に頼っている面、合理性を伴わない社会的階級に影響された行動をとっていたり[^ssk]、両者ともにパブリックイメージと現実との大きな差が存在していた。つまり同じリサーチという言葉で表される行為の中でも、誰が実質的に何をやっているのかというカテゴリ分けが職能や肩書きをベースにしたものではもはや機能しなくなっているという背景があった。そこでフレイリングはアーティスト、デザイナー、科学者に共通して行われている営みをinto、through、forという視点でいちど結合、再分解することでデザイナー（あるいは、リサーチャーという個人）が今何をすべきかへのヒントを見出そうとしていた。

[^ssk]: フレイリングはこの動向の例として社会構築主義的科学論の代表的立場である科学知識の社会学（Sociology of Scientific Knowledge：SSK）の論者の1人、ハリー・コリンズを例に挙げている。

今日のResearch through Designという用語の定着そのものは、カーネギーメロン大学の研究者ジョン・ツィマーマンのような、デザインをバックグラウンドに持ちつつもコンピューター科学の分野で活動する研究者らが、自らの学問領域を明確にするためフレイリングの議論などを援用することで立ち上がってきた[@Zimmerman2010]。RtDの解釈は研究者によって異なるところもあるが、本章の流れに沿って説明すればその特徴は、既に挙げた自己反映性への自覚に起因する2つの転換、**問題解決主義（Solutionism）から問題提起へ**と**客観的観察から共同参加/あるいは介入**である。

### 問題解決主義（Solutionism）から問題提起へ 

RtDにおけるこれまでのデザイン研究からのひとつの重要な転換は、ユーザーや社会的な問題を解決することを目的とするのではなく、人工物を通じて問題に対しての議論を引き起こしたり、あるいはこれまで着目されてなかった問題を周知することを目指す、デザインにおける批評性の重視である。この批評性の重視という側面では、RtDの中でも特にクリティカル・デザインやスペキュラティブ・デザインといった分野がHCI研究にも関わる領域として存在する。マルパスはこのような批評性を強調する源流に、1960年代のイタリアを起点としたアンチ・デザインのような反商業主義的デザインを見出している[@Marpus2019]。

例えば、クリティカル・デザインとスペキュラティブ・デザインという言葉を提起したひとりであるデザイナーのアンソニー（トニー）・ダンと、HCIの分野においてRtDの批評的側面を問い続けてきたウィリアム（ビル）・ゲイバーは1997年にHCI分野の国際会議CHIで 『The Pillow：デジタル時代のアーティスト・デザイナー』というタイトルの論文を発表している[@Dunne1997]。The Pillowは身の回りの電磁波に反応して表示パターンを変えるLCDスクリーンが埋め込まれた枕の形のプロダクトである。もちろんこの枕は実際に製品として売りに出されることを目的としているわけではない。ダンとゲイバーはこのThe Pillowという人工物を通じて、当時のインターネットや携帯電話の普及に際して変化しつつある、電磁波という物理的障壁を超えて飛び交うデジタル情報によるプライバシーの意識の変化を顕在化させることを試みたのだ。もしこの枕を置いて眠ろうとした時に、隣の家で誰かがテレビを付けたことをThe Pillowが感知し光ったとしたら、知らない隣人の生活が電磁波を通じてこの家に侵入してきたことになるだろう。The Pillow自体が実際に使われることはなくとも、その人工物にはある種のフィクションとして今後起こりうるであろうプライバシーの概念の変化の可能性を伝える説得力が存在している。このように、問題を解決するよりもこれまで気付かれていなかった問題を提起することがResearch through Designにおける1つの特徴である。

もっとも、現在のHCI分野においても問題解決主義が完璧に否定されたわけではなく、2010年以降もHCI分野においては問題解決主義とRtDは同居し続けている。例えば2016年オーラスヴィルタとホーンベックの論文のように、「HCI研究とは問題解決である」と言い切るメタ研究も存在する[@Oulasvirta2016]。とはいえこうした主張においても、デザイン対象が作られた後にリサーチクエスチョンが構成されることを認めていたり、あるいはこれまで考えられていなかったコンセプトを提示すること自体、ゆくゆくは解決されるべき問題を提示しているため問題解決の一部である、と捉えており、RtD的な考え方との接近を見せている。

<!-- UCDへの言及？ -->

### 客観的観察（Objectivism）から共同参加/あるいは介入

RtDにおけるもう1つの重要な視点は、デザインされたものを使う人：ユーザーをデザイナーが観察することで問題点を洗い出すという図式を否定し、これまでユーザーと呼ばれていた人たちを共同でものを作る人として巻き込んでいく、あるいはユーザーの生活空間に積極的に介入していくという転換である。この観点で代表的に着目されるのが、やはりゲイバーやダン、そしてエレナ・パセンティらが提案した**Cultural Probe（文化的探針）**という考え方である。ゲイバーらは、ちょうど電子回路にオシロスコープのプローブを当ててそこに流れる電圧や電流を測るように、ある文化圏やコミュニティに対する理解を深めるための方法としてこのCultural Probeを提案した。Cultural Probeにはポストカードや地図、使い捨てカメラなどを、質問や使い方のインストラクションが封入されている。例えばポストカードには「あなたが大事にし続けているアドバイスや気付きについて教えてください」といった質問、地図にはよく1人で行く場所、誰かと会うために行く場所などをマークしてもらう、カメラには今日初めて出会った人やあなたが今日着るつもりの服を撮ってもらう、などが書かれている。こうしたキットをある地域のコミュニティに届け、一定期間後に送り返してもらうのだ[@Gaver1999]。

こうしたProbeの返信を収集した結果、ゲイバーらは送った地域におけるいくつかの社会問題を顕在化させるに至っている。しかし重要な点は、ゲイバーらは問題発見や質的調査のための方法としてこのProbeを提案しているわけではないということだ。

この背景を考えるためには、同時代におけるユーザー中心デザイン（User-Centered Design：UCD）という動向において、製品設計においてユーザーの抱えるニーズや問題をユーザー本人が正しく把握していたり表現できているわけではないという状態へのアプローチのひとつとして、文化人類学者が一定の功績をなしてきたことなどを理解しておく必要がある。代表的な例としては1984年の『プランと状況的行為』で人類学者のルーシー・サッチマンがゼロックス社PARCにおいて、自動コピー機の利用を支援するシステムの実際の利用状況をエスノメソドロジーの方法論で分析した研究が挙げられる[@Suchman1999]。エスノメソドロジーとは概念化されていないレベルでの人間の慣習的行動を会話分析などを用いて明らかにしようとする学問である（サッチマンの研究では映像記録も用いている）。サッチマンは人間の行為が、サイバネティクス的慣習で考えられている、入出力を持った静的システムとして常に計画された行動をとっているわけではなく、常に状況に依存した行動（Situated Action）を取っていることを示した。この研究は、デザイナーの意図通りにユーザーが行動してくれることなどないという現実と、実際の利用とかけ離れた環境における実験ではなく、実際の利用の現場を事細かに観察、分析することの重要性という2つの意味で大きな影響を与えた。1980〜1990年代にはPARCや、アップル、インテルのようなコンピューター技術を開発する企業がサッチマンのような人類学者を招く、もしくは雇うことで、ユーザーのより深い理解を目指す流れがあった。

そうした意味でCultural Probeは、実験環境とは異なる形でユーザーが日常的に抱える潜在的な問題を把握するための便利なツールとして、（特にヨーロッパ圏の）デザイン研究で広く普及した。しかし、コスキネンらが指摘するように、Probeはあるコミュニティを理解するためのツールというよりも、むしろプライベートな贈り物や手紙のやり取りに近いものであり、あるコミュニティへの積極的介入や新しい交友関係を結んでいる側面が十分に理解されていない[@Koskinen2011,p41]。

実際、ゲイバーはCultural Probeの着想元の1つに1960年代のダダやシチュアシオニストのような、ギャラリーや美術館のような既存の発表の場に留まらず、日常生活へと介入する芸術表現を模索した動向を挙げている。これに加えThe Pillowのような議論を喚起するデザインの例との関係性を鑑みても、ゲイバーらの狙いの1つは、デザイナーが物づくりを通じて社会に介入していることに自覚的になることだと言える。それはつまり、水面に波紋を全く起こさないまま針を落とすことなど不可能であるように、客観的なユーザーの理解ができないのであれば、むしろ積極的にユーザーと呼ばれていた人たちの生活の中へ介入していくことを意識的に行うべきだという主張である。

## 音楽とコンピューティングにおけるRtDの受容

しかしながらResearch through Designは依然、デザイン思考に起きた方法論としての固定化と似たように、結果的にコンピューター科学という領域における、研究における問題設定とその評価のためのフレームワーク程度に見積もられてしまっている現状がある。特にそれはデザインリサーチ的手法が一般的に受容されていない周縁的分野——例えば我々のような音楽とコンピューティングにおける研究になるほど顕著に現れる。

例として、筆者の研究対象である音楽のためのプログラミング言語研究における、西野によるLC言語の設計をRtDの側面からの分析した論文を取り上げる[@Nishino2012]。西野は音楽プログラミング言語設計という行為が、音声合成の手法の確立などの研究と比べれば、実用的なツールとしての目的意識と評価という側面が強く、知への貢献という側面が十分に取り上げられていないという問題意識をツィマーマンらによるRtDの文献を参照しつつ提起する。西野が開発するLC言語は、microsoundという、音声データを数ミリ秒単位に切り刻み再構成するような音声合成の手法[@Roads2003]が既存の言語では十分に表現できないという具体的事象から、mostly-strongly-timed languageという新しい音楽プログラミング言語における概念の創出ができているという具体例を示している。しかしながらこの研究ではツィマーマンがRtDの解説で多用していた「世界を現状から好ましい（preferred）状態へと変化させる」という部分が強調されすぎて、なぜローズが提案したmicrosoundという手法がコンピューター音楽において重要なのか、という未来の音楽制作のビジョンは所与のものとされている。

このPreferred Stateという用語はサイモンのデザインサイエンスから部分的に肯定できる部分として用いられたものであり[@Koskinen2011,p42]、ツィマーマンが意図していたところはより自己反映性への自覚であった。RtDでははじめから問題が設定されているのではなく、常に仮定の問題からスタートしつつも作る過程で問題が浮かび上がる。このデザインサイエンスと異なるアプローチとしてのRtDは、世界が自己へ反映され、自己の行動が世界に反映されるというループへと自覚的になることが要点であり、好ましい世界の状態とはそもそも何かについての反芻が欠けてはならなかったはずだ。そういう意味では西野の研究は自己反映性への言及が少なく、依然単なる問題解決のための手段としてのPLfMの開発にとどまっている。

こうした例に限らず、RtDはその語の浸透に比して、というよりも浸透とともに議論がデザインの言説から応用領域へ離れていくにつれ、デザイン思考と似て研究プログラム（どのような価値基準をもとに研究を進めるか）ではなく研究メソッド（どのような手段をもって研究を進めるべきか）として受け取られるようになってきた面もある。

# 歴史を作り直すデザイン

![オージャーによる、Alternative PresentとSpeculative Futuresの概念を表した図[@Auger2010]。](img/auger_alternativepresent.pdf){#fig:auger width=90%}

さて、Research through Designのアプローチは例えばクリティカル・デザインやスペキュラティブ・デザインの文脈ではサイエンス・フィクションから影響を受けてきたように、作った物を利用している状況を映像作品として提示するなど、物語を有効活用してきたという特徴も挙げられる。こうした物語のデザインへの活用は特にスペキュラティブ・デザインでは『The Pillow』のように、未来のありえるかもしれない技術の姿への想像力を喚起するためのツールとして人工物を用いることが多い。しかしサイエンス・フィクションは未来の姿を想像するだけでなく、過去への探索をきっかけとして、例えば電気技術ではなく蒸気機関が極端に発達した世界を描くスチームパンクのような、並行世界の現在の姿を描きだすという立場も考えられる。デザイン研究者のジェームズ・オージャーはこの違いを[@fig:auger]のように、*ありえるかもしれない未来（Speculative Futures）*と、*ありえたかもしれない現在（Alternative Present）*という違いとして表している[@Auger2010]。

オージャーが指摘するように、未来を思索するデザインは、時に現実性から離れすぎることによって人々の共感を得られなかったり、逆に単に物語を作る者の現在の現実に対するステレオタイプ的認識を強調するだけにしかなりえない危うさがある（いったい何人のデザイナーが2019年以降のパンデミックの姿を想像できただろうか？）。実際、フィクションを用いた未来の思索とは期待の社会学の説明（[@fig:brown]）における2.約束作りのプロセスそのままとも解釈でき、結局は未来予測を作るという建前で、実際には無意識に社会的要請に応えているだけという状態にもなりかねない。

その点において、過去に参照点をおいたプロジェクトは、提示された社会や文化が現在の姿とかけ離れていても、逆説的に**なぜ現在そうした社会や文化にわたしたちは至らなかったのか**、という問いの機能が保たれ続ける。

本研究で指向するのはResearch through Designの中でも、このような、過去へのリサーチから異なる歴史を想像するためのデザインをさらに押し進めた立場–異なる歴史を*想像*するだけでなく、*創造*するという立場である。歴史を創造するとは一見事実の改竄のような不誠実な印象を与えるかもしれない。しかしクーンのパラダイム論以降、科学論が反証可能な命題への固執をやめたように、絶対的な歴史的事実というものもまた存在しない[^history]。

[^history]: もちろん、この主張にはかなりの危うさがつきまとっている。歴史的事実の絶対性が揺らぐということは、原理的にはロスナーのように、これまで記述されなかった部分に光を当てる意義を持つと同時に、あった筈のものさえ無かったことにされてしまう危険性を認めることに繋がるからだ。そしてそれは大きな権力を持つ集団であるほど有効に働いてしまう。だがわたしたちにはその前提を受け入れた上で行動する以外の術は残されていない。

それどころか、わたしたちはテキストに限らず、今日であれば映像、音声、そしてウェブサイトのような（プリミティブなものも含めて）様々なテクノロジーを通じて現実や歴史の認識を形作る。いわば無数の過去のデータの集合が、わたしたちの現実認識を生み出しているのである。であれば、過去存在はしていたが着目されてこなかったテクノロジー、あるいは時代遅れとされ注目されることのなくなったメディアテクノロジーを、現代において作り直すことでわたしたちの歴史や現実の認識自体を作り替えることもまた可能であり、単一的な方向へ進む技術発展に異なる可能性を見出すための手段となりうるはずだ。

そこで、歴史を作り直すデザインの参照点となる、ロスナーの批判的奇譚づくり（Critical Fabulation）と、メディア論における1つのアプローチ、メディア考古学をインタラクションデザインのアプローチと掛け合わせたメディア考古学的制作という2つの取り組みを紹介する。ここでは、筆者が過去行なってきた作品制作と本研究の連続性についても触れる。これらのアプローチを参考に、PLfMの設計と実装を歴史を作り直すデザインとして提示する必然性を示し、本章をまとめることにする。

## ロスナーの「批判的奇譚づくり」

デザインやHCIにおける編み物やキルティングのような手工芸との関わりを研究してきたワシントン大学のダニエラ・K・ロスナーは、RtDも含めたこれまでのデザインの文脈と異なる方法論として、「批判的奇譚づくり（Critical Fabulation）[^criticalfabulation]」という考え方を提唱している。

[^criticalfabulation]:「Critical Fabulation」 の訳出は、この語の起源、ダナ・ハラウェイのSFという語の読み替えのひとつである「Speculative Fabulation」の訳を参考にした。猪口による論考では「思弁的寓話小説」[@Inoguchi2018]、逆卷による2016年のハラウェイのインタビューの翻訳では「思弁的奇譚」とされており[@Sakamaki2019]、後者を参考にしつつも、ロスナーの文献内ではその奇譚を作る、語るという動詞的意味合い（Fabulating）が強調されているため「批判的奇譚づくり」とした。

ロスナーはデザイン・サイエンス、デザイン思考、RtDの歴史的文脈を振り返った上で、既存のデザイン研究のパラダイムに浸透する4つの考え方を批判した。1つ目は普遍主義（Universalism）のようなすべての問題に対応できるような万能の解決策を提示しようとすることであり、これはデザイン・サイエンスの運動から意地悪な問題の提起によって否定されてきたものと対応する。2つ目は客観主義(Objectivism)、すなわちデザインを使う対象を客観的対象として決して影響を与えることなく観察する、いわば神の目線的に捉えることで問題を洗い出そうとする立場だ。これはデザインサイエンスの時代における考え方とも一致するし、デザイン思考的、ユーザー中心デザインにおいてもユーザーを客観的に理解可能な対象として捉える見方は続いてきた。3つ目は問題解決主義（Solutionism）である。これは、デザイン思考からクリティカル・デザインのような問題提起をするためのデザインという転換で否定されてきたものだ。ここまではRtDまでのデザインの潮流の変化としてすでに説明してきたことだ。だがロスナーはさらに、Research through Designも含めた既存のデザイン文化には、技術を使ったり作ったりする主体をこれまでのパラダイムで言えば、ユーザーやデザイナーという形で（仮に参加型のデザインのような性質を持っていたとしても）あくまで個人の集合として捉えている**個人主義（Individualism）**が強く根付いていると指摘する。

<!-- （この4つの批判に関しては図に入れたり冒頭からの説明に入れてしまったほうがわかりやすいかも） -->

ロスナーはこの個人主義の存在をフェミニズム的視点と動機から説明する。例に挙げるのは1960年代冷戦下のアメリカにおける世界初の有人宇宙飛行を実現したアポロ8号において、ロケット制御のためのコンピューター：アポロ・ガイダンス・コンピューター（AGC）のプログラムを記憶した、磁気コアメモリ(より正確には、コアロープメモリと呼ばれるもの)のという記憶装置の製作である。磁気コアメモリは電線をコアと呼ばれるリング状の磁性体に通し、そこへ電流を流し、電流が引き起こす磁場によってコアの磁気極性を変えることでバイナリデータを保存する記憶装置である。トランジスタが安価になる以前の当時の技術環境においては、磁気コアメモリは物理的に小さく、ロケットの中という物理的振動や熱が激しい環境においても比較的安定して動作するために主記憶装置として採用された。この磁気コアメモリは、なるべく集積密度を上げるために非常に小さなコアに細いワイヤを通して作られるが、その製造方法は最後まで完全には自動化されず、特にアポロ計画のためには服飾工場や時計の製造工場で働く女性工員が生産を担っていた[@Shriff2019]。

有人(**Manned**)飛行で、初の月面往復という革新的事業はこれら多くの無名の女性による集団的創造プロセスなくしては成立し得なかったが、こうした作業はAGCのアーキテクチャを作ったり、あるいは実際にロケットに乗ったりした人と比べると歴史の記述には残りづらい。それは、手作業の中にも、コンピューターアーキテクチャを設計する作業と同じく存在しているはずの様々な知識が、身体的技能と結びつき言語化されないレベルでのもの–フレイリングの分類で言えば共有可能でない知、Research *for* Art/Designと呼ばれていた部分が歴史の中には記述されえないからである。

ロスナーらはこうしたテクノロジーにまつわるヒロイックな言説に基づいて構築された個人主義的歴史像が今日のデザインにも強く根付いていることをひとつの動機として、磁気コアメモリを導電糸やビーズを用いてテキスタイルとして作成する『Making Core Memory』ワークショップを行った。4×4の磁気コアビーズにはデータが実際に保存できるようになっており、ワークショップの中ではそのデータをもとに音楽を鳴らしたり、テキストデータとして保存されたデータをTwitterに投稿するなどの応用を交えてその反応を記録した[@Rosner2018chi]。

ロスナーらのプロジェクトはダンやゲイバーらのクリティカル・デザイン/スペキュラティブ・デザイン同様に、直接的に役に立つプロダクトを作っているのではなく、デザインされたものを通じて問いかけを行うことを目的としているという点では共通している。しかし、その問いかけはありえるかもしれない未来の姿について夢想するためのものではない。そうではなく、これまで歴史の中には記述できなかったコアメモリを作るという手作業を通じたコミュニケーションを引き起こすことで、あったはずなのに認識できていなかった、輝かしい個人の功績とは真逆の無数の人々の関係性の中に現れる技術的貢献や、そもそも記述されないため存在しないことになっていた歴史像を浮かび上がらせる試みである。

## メディア考古学 {#sec:mediaarch}

また、ロスナーとは異なる視点で[^rosnerarch]過去への積極的な調査を基に人工物のデザインへのヒントを得るために、既に使われなくなったり廃れたメディア装置への探求というアプローチ、メディア考古学を援用してきた者もいる。

[^rosnerarch]: RosnerはMaking Core MemoryプロジェクトやCritical Fabulationの説明においてメディア考古学にはほとんど言及していないが、CHI2018での発表の中では考察の中でユシー・パリッカの名前を挙げ限定的に関連性を見出している[@Rosner2018chi,p10]。

メディア考古学とはそれ自体が明確な定義を与えられることを嫌うような性質を持っているため注意を要する用語ではあるが、本研究での定義は**歴史の中に埋没したメディアを掘り返すことで、所与のものとされている歴史に別の物語を与えるアプローチ**としておく。メディア考古学の中でも代表的なものとして、1980年代や1990年代以降のエルキ・フータモが試みて来た、映画や映像メディアの正史には普通記述されない万華鏡のような装置を掘り下げることで、最新テクノロジーへの熱狂の繰り返しの萌芽を見出す研究[@Huhtamo2015,p83]などがある。

大久保はメディア考古学研究群のアプローチに存在する微妙なスペクトラムを、メディア環境を形成する要因を「社会-技術」のどちらで捉えるか、また学術的貢献の形として「歴史-理論」のどちらに重きを置くか、という2つの視点で整理している[@Okubo2021,p285〜289]。大久保によれば、この視点はどちらもメディア考古学に共通する思想的背景となっているフーコーの『知の考古学』の解釈に大きく影響されるとしている。[@fig:mediaarch]にこの立場の広がりの概念を示した。

![[@Okubo2021]をもとに作成した、メディア考古学の立場の広がりを示した図。](img/mediaarchaeology_position.pdf){#fig:mediaarch width=80%}

横軸である「社会-技術」の軸では、作られたメディアテクノロジーが既存の社会的言説の影響のもとに生まれると考えるか、メディアテクノロジー自体がテクストではない形で（たとえばフリードリヒ・キットラーの例を借りれば、レコードや映画、タイプライター[@Kittler1999]が）思考や言説を形成すると考える違いがある。この中でも「社会」寄りのアプローチとしては、キャロリン・マーヴィンの『古いメディアが新しかった時』[@Marvin2003]に代表される、STSにおける社会構築主義的立場の1つ、社会の技術的構成（Social Construction of Technology:SCOT）という領域とも重なる。SCOT的研究の中にはそれほど埋没したメディアの掘り下げといった側面を含まず、あくまでテクノロジーが社会的要請によって決定されるというアンチ技術決定論的側面の方が大きいものも含まれる[^scot]。

[^scot]: SCOTの中で本研究と関連するものとしては、たとえばピンチとトロッコによるモーグ・シンセサイザーの歴史的記述を行った『Analog Days』[@Pinch2004]、電子楽器用プロトコルMIDIの規格成立過程を追いかけたディドゥックの博士研究及び『Mad Skills』[@Diduck2018]のような研究が挙げられる。主に第3章で参照する。

一方縦軸の「歴史-理論」の軸では、これまで取り上げられなかったメディア装置の一次史料の収集と記述に重きを置く、より歴史学的なアプローチか、既存の史料の中からの選択をし直すことで歴史的記述を再考することに重きを置いているとされる。（もっとも大久保も強調しているように、この立場の広がりは対立しているものではなく、論者によって力点を置く場所が違うということで、あくまで多様なアプローチがあるメディア考古学という領域の見取り図として機能はする、という程度のものだと考えた方がいい）。

メディア考古学はメディアの歴史や、メディアがわたしたちの身体や知覚に及ぼす影響を考察するためのフレームワークという側面が大きい。とはいえ、使われなくなったメディアに着目することは、ニューメディアアートやインタラクションデザインなどにおける作品制作のアプローチとしてメディア考古学という概念が立ち上がるよりも前から行われ続けてきた。フータモは岩井俊雄のゾートロープ的装置を拡張する『時間層』シリーズのような作品群や、ポール・デマリーニスの『エジソン効果』の中で陶器の壺に刻まれた溝をレコードとして扱い音を読み出す試みのような芸術家の取り組みを、メディア考古学的実践のひとつとして位置付けている[@Huhtamo2015,7章]。同様にパリッカとハーツがサーキット・ベンディングという電子回路を意図的に壊すことで楽器として用いるアプローチを分析している[@Hertz2012][^bending]。これらの分析には作家の意図に関わらず、いわば後付け的にメディア考古学と評される場合も含まれる。例えばデマリーニスの場合は作品制作の中のリサーチにで過去の期限の切れた特許資料の中からアイデアを得ていたり、明確に過去のメディアに対するリサーチを行っている。一方で、サーキット・ベンディングのようなアプローチは実践している者からすれば面白い音が鳴るように回路を改造しているだけという側面も強い。

[^bending]: [@sec:failure]も参照。

その上で近年では、作品制作にメディア考古学の方法論を明確に自覚して用いるプロジェクトが現れてきている。たとえば第1章で既に例示した、情報科学芸術大学院大学（IAMAS）において城一裕が中心となって活動した『車輪の再発明』プロジェクト[@Jo2016]や、NIMEのような楽器制作の方法論の文脈でもジャコモ・レプリの『Cembalo Scrivano』[@Lepri2018]のような例があらわれている。本稿ではこのような、メディア考古学的視点を自覚的に作品制作のプロセスに導入する立場を**メディア考古学的制作**と呼ぶ。

何より、筆者自身が意図的にメディア考古学を作品制作の方法論として用いてきた1人である。例えば磁気コアメモリよりもさらに古い1950年代の電子計算機黎明期に用いられた、音響遅延線メモリーと呼ばれる音波のフィードバックループを用いてデジタルデータを保存する記憶装置を空間に開かれた形で再構築するインスタレーション作品『送れ｜遅れ / post｜past』では、物質的状態を固定しないままにデータを保存する音響遅延線メモリを物理的に分離された2台の通信装置として構成することで、通信と記録の不可分性を顕在化させた[@Matsuura2016]（[@sec:delaymemory]も参照）。

別の例を挙げれば、筆者が2018年に、第1章冒頭で説明したSFPC滞在中に作った『Electronic Delay Time Automatic Calculator（EDTAC）』（[@fig:edtac]）がある。EDTACは、「はじめからコンピューターの設計の中に時間の概念が組み込まれていたらどうなっているか」という問いを提出するために作られた、極めてプリミティブな計算機である[@Matsuura2018;@Matsuura2019,第4章]。現在使われている一般的なコンピュータは音楽のように時間に関係する処理を日常的に行っているにもかかわらず、その理論的基盤には時間の概念が一切含まれていない。EDTACはプログラムされた通りに時間を分割しクリック音を鳴らし続けるだけの機能しか持っていない。しかしちょうど世界最初の電子計算機であるENIACがケーブルを配線し直すことで物理的にプログラムを構成していたように、抵抗の内蔵されたケーブルと光ファイバーという物質的接続によって分割する時間間隔が決定される、というように、ハードウェアレベルで時間操作がその中核に組み込まれている。EDTAC手で作られた回路彫刻として提示され、全く異なる形の計算機の存在の可能性を問いかけるようになっている。

![Electronic Delay Time Automatic Calculator（EDTAC）（2018）。撮影：Filip Wolak](img/edtac-filipwolak.jpg){#fig:edtac width=80%}

こうしたメディア考古学的実践を今日のデザイン研究の中に位置付けるにあたり注意を要し、かつ自分自身も不満を残し続けてきたのは、メディア考古学的制作における作者や作品といった単位の問題である。クリティカル・デザインのような未来についての問いかけを行うデザインは、現実的には役に立ちそうもないものだからこそ、その発表の場としてギャラリーや美術館という場所が選ばれる。このことはメディア考古学的制作をデザインのアプローチとして用いる場合にも共通する点だが、2つの点で問題を招く。ひとつはCultural Probeで問題意識に据えられていたように、ギャラリーのようなあらかじめ美術を想定して作られた場にデザインした物を置くことによって、それは人々の日常生活から離れて、単に鑑賞の対象となってしまうことである。もうひとつはロスナーが批判した個人主義のように、デザインされた物とデザイナー個人の記名性が過剰に結びついてしまい、デザインの内容そのものよりも誰がどういった内容の作品制作を続けているかという点に重きがおかれ、社会の中におけるデザイン運動の中の流れの1つとして捉えることが難しくなってしまうことだ。

メディア研究者の秋吉康晴は『車輪の再発明』プロジェクトの発端となった、レーザーカッターを用いてレコードの溝をデジタルデータから直接生成する城の作品制作の分析を通じて、メディア考古学的作品制作の既存の言説が過度に作者性と結び付けられていることを指摘している[@Akiyoshi2020]。例えばメディア考古学的作品制作の代表例としてフータモが例に挙げやポール・デマリーニスの製作の背景には1960年代、つまりサイバネティクス全盛期における、アメリカ西海岸のヒッピームーブメントと結びついたDIYテクノカルチャーの存在があった。メディア考古学としてのサーキット・ベンディングについても、パリッカらの研究ではリード・ガザラのような、ムーブメントの中での代表的存在が過度に照らし出されている一方で、実際には存在していたはずの、個人間レベルの技法や機材の共有のような集団的創造プロセスの側面が薄められてしまっている。

秋吉はつまり、フータモやパリッカらはアーティストやサーキットベンダーをいたずらに特別視しすぎており、歴史に個人としては記述されないDIYの実践家との接続を結果的に断ち切ってしまっていることを指摘したのだ。その一方で城の作品制作は、技法自体の公開やドキュメント化を通じて、よりどんな個人でもその制作の再現やさらなる飛躍のための余白が残されている。

この視点を踏まえた上で、『車輪の再発明』プロジェクトを改めて見ると、城の他のプロジェクトと比べても、作者やオーサーシップといった概念はより慎重に取り扱われている。プロジェクトの中では、参加した学生や教員によって多数の「作品」に相当するものが作られ、それぞれにタイトルもつけられているのだが、それだけではなく制作の中で共有して使われた「技法」にもタイトルが付けられている。例としては、技法の名前として『予め吹きこまれた音響のない（もしくはある）レコード』がまず存在する。そして、その技法を用いた実例として、城による、溝が刻まれた扇型のアクリル板を組み合わせることでレコードをステップシーケンサーのように扱う『断片化された音楽』、大島によるレコードの溝の上に坂道が形成され、針がスキージャンプのように飛び出すことでランダムに次に再生される溝が変わる『飛び出せ↑レコード』のような多数のバリエーションが存在する。城はこの技法に名前をつける行為について「作品とツールの間の中間層」を、技法という名のもとに提案することを試みたと説明している。

ロスナーの個人主義批判を踏まえれば、メディア考古学的制作に内在する問題点とは、アーティストを特権視するだけでなく、作品（や何らかのDIYムーブメントなど）を特定の個人的アイデンティティに結び付け過ぎてしまうということでもあると理解できるだろう。そして、技法に名前をつける行為は、ギャラリーのような場所で展示されることを踏まえた上で、作られたものの集団的オーサーシップを表明するための役割を持っている。

多くの場合、作者性の強調と創造プロセスの個人主義的解釈はにまつわる問題は、作られたものを分析する側に内在する。とはいえ制作をする側にも、特にギャラリーや美術館のような展示というフォーマットを選ぶことによって個人主義的視点を内面化してしまうリスクがつきまとう。それゆえ、ロスナーのワークショップの形式や、『車輪の再発明』での技法の名付けのように、作られたものをどう提示するか、どうプロジェクトの外側の人間と接点を作るのかはメディア考古学的制作におけるひとつの課題である。

本研究における音楽のためのプログラミング言語の開発という行為は、対象が道具という、作品以前の存在である。それゆえ、典型的なデザインや工学の文脈に置かれると問題解決主義的視点で捉えられがちである。かといって問題解決主義を否定する、議論を起こすことを目的としたクリティカルデザインのプロジェクトのように美術館やギャラリーのような場に置かれることもまたそぐわない。

それゆえ、本研究は以下のような方針をとるのである。まず、本研究の主題はあくまでmimiumという言語の開発である。そして、mimiumという言語の開発自体は実用を意識してもいる。しかし、研究としてはツールとしての実用性を直接的には問わない。そうではなく、ツールを作る事によるデザイナー自身の視点の変化を織り込んで、その道具に関する歴史認識を再構築することを目指す。歴史的視点の変化と、そのツールがどういった社会や文化の中で使われるべきかを議論する事によって、「実用性」の価値判断自体の基準自体も自ずから変化してくるだろう。

こうした研究プログラムは、PLfMに限らないより広い対象にも適用できる。特に表現のための道具作りのような、その主題に技術的要素が深く関わっているが、定量的/定質的どちらでもその効用を記述しづらい対象の研究には、工学的な問題解決に偏った評価でもなく、かといってその道具を使って作られるコンテンツだけに着目するのでもない新しいアプローチとして利用できるものとなるだろう。

<!-- （音楽土木工学という学問における研究のあり方である位置付け、一般的な工学的なアプローチとは随分違うので トランジションデザイン） -->


# 小括 {#chap2end}

ここまでの議論を振り返り、本研究の立脚点を改めて確認しよう。

本章ではまず音楽土木工学という学問を、音楽のためのプログラミング言語を実装する過程で描きだすという研究のあり方を、主にデザインリサーチの変遷を追いかけることで位置付けた。

デザインリサーチは、大きく分けて1960年代においてサイバネティクスの影響を受けた、デザインサイエンスにおける科学的、普遍的問題解決手法の探求、1970年代以降のデザイン思考のような、個人的省察による問題解決、1990年代以降のResearch through Designにおける問題解決から問題提起、客観的観察から積極的介入といった変遷を見ることができた。

中でもRtDの文脈を引き継ぎ、未来よりも過去に着目する、ありえるかもしれない現在技術・メディア環境を想起させるメディア考古学的制作、これまで歴史的事実の中に含まれなかった身体化された知や周縁化された社会集団に光を当てることで歴史認識を作り替える批判的奇譚づくりといった事例を紹介した。過去の言説や、通常メディア表現には無関係とされるようなインフラストラクチャに着目することで、メディアテクノロジーの進むべき方向性に異なる可能性を見出すための契機としてのデザイン行為として本研究を位置付けた。

このデザインの行為の変化に通底する視点として重要なのが自己反映性（Reflexivity）への自覚である。道具や作品、人工物を作り出すことは世界や社会に対して何らかの影響を与える、常に中立ではない政治的行動である。ユーザーを神の目線で客観的に観察することなどできない。

ここでRtDの言葉が作られる経緯となったフレイリングのアート、デザインにおけるリサーチ行為のカテゴリ分けを再訪すると、フレイリングはinto、through、forの違いを次のようにも言い換えている。

- INTO： *How can I tell that I think till I see what I say?*（どうして自分が考えてることを、自分が言うのを観測する前に知ることができるだろうか？）
- THROUGH： *How can I tell what I think till I see what I make and do?*（どうして自分が考えてることを、**自分が作ったものを観測する前に知ることができるだろうか？**）
- FOR： *How can I tell what I am till I see what I make and do?*（**どうして自分とは何なのかということを、自分が作ったものを観測する前に知ることができるだろうか？**）[^forster]

[^forster]: この原典（INTOに対応するものがオリジナル）はフレイリングによれば小説家E.M. フォースターのおばが彼に言ったこととされている有名なフレーズだが、実際のところ参照元がはっきりしないことでよく知られている。1926年のグラハム・ウォラスによる『The Art of Thought』がフォースターよりも早いものとして挙げられているが、この文のような考え方は当時のヴィトゲンシュタインの『論理哲学論考』に代表される哲学の言語論的転回（言語が現実世界を構成すると考える哲学の運動）を反映したものだと言える。  https://quoteinvestigator.com/2019/12/11/know-say/ 2021年12月12日最終閲覧。

つまり、この区分は実際のところカテゴリ分けというよりも自己反映性の強さの段階わけに近いものだった。そして、フレイリングがいばらの道（thorny）かつ最も探求すべき場所していたのは、実は*through*よりも*for*（自らの体験に基づき身体化された知）なのだ[@Frayling1993,p5]。ものを作る過程で現実が構成され、社会が構成され、また自らが構成される。こうした知の形をフレイリングは共有可能な知としてカウントしていなかったが、それはメディア考古学の視点を導入すれば、もしかすると単にテクストの形を持たず、別のメディアの中に埋め込まれた言説として取り出せるかもしれない。あるいはロスナーの指摘を踏まえれば、集団の中で共有はされていたが歴史の中に記述されえなかったもので、実際に手を動かしてみることで、改めて身体化された知として復活（Recuperate）させられるのではないだろうか。

本研究で筆者はこうした視点に基づいて、実際には音楽のためのプログラミング言語というデザイン対象を取り扱う。これは、音楽のためのプログラミング言語を作る、もしくは音楽のためにプログラミング言語を作ることで、音楽家がコンピューターを用いて音楽を作る時の認識論を明確化できるのではないかという観点に基づいている。あるいは、音楽が流通する社会における音楽を下支えするインフラストラクチャの政治性を明確にできるのではないかという観点でもある。次の章ではそうした、なぜ音楽のためのプログラミング言語という対象なのかという理由を、メディアとしてのコンピューターの扱われ方の歴史的変遷を辿ることで明確にしていく。