
Epistemic Tool

Epistemic Thing

# Andrew Sorensen

Cyber-physical Programming

特に

、またそれを引き継いだ、PinchとBilkerに代表される技術の社会構築理論(Social C onstraction of Technology:SCOT)


デザインと並んで芸術実践、ラボラトリーにおける研究においても

ありうる(Possible-Plausible)未来の可能性の中からもっとも現状のままでは起こりやすそうな(Probable)未来を、望ましい(Prefereble)未来の方向へと少しでも変えていくという未来へ目線を向けたもの、あるいは、過去の
対象の拡大：

方法論の拡大：


水野はこれを[#fig:pyramid]のように表している。こうした傾向は、ユーザー個人の行動や経験に対するデザインだけでは複雑な利害関係が絡み合う意地悪な問題に対処できないことへの対応として見て取れる。

こうした大きな社会問題を射程に入れたデザインのアプローチとしては、DunneとRabyによるスペキュラティブデザインに代表される、並行世界の未来に存在しうる人工物を作り出し、その鑑賞者に議論を促すような方法論が長く培われてきた。

また1つの解決策によって即効的に1つの問題が解決できず、解決できるとしても時間がかかることを認めた上で取れるアプローチ

音楽にまつわるテクノロジーという領域においてもこうした傾向を反映することは必要になってくるはずだ。特に、プログラミング言語は序章で述べたように、完成という概念がもともと希薄であり、時間をかけて少しづつ変化していく人工物であるという視点は、カーネギーメロン大学が提示したTransition Designという潮流などにも呼応する。



---

本論文は、音楽のためのプログラミング言語mimiumの設計と実装を通じて、音楽のためのプログラミング言語(Programming Language for Music:**PLfM**)を作るという行為の概念化を試み、その上であるべきコンピューターと音楽の関係性を考え直すものである。

本論文で議論する「音楽のためのプログラミング言語」は、テキストや人間が知覚、操作可能な記号体系を用いて[^defplfm]コンピューターで音楽を生成するための人工言語である。

[^defplfm]: 人間が知覚、操作可能な記号体系という遠回しな表現を用いるのは、（とくに音楽を扱う）プログラミング言語の中には、Maxのようにテキストではなく、入出力のあるボックス同士をマウスやタッチパッドなどでつないでいくことでプログラムを構成するものがあるからである。

プログラミングを用いた音楽表現は、リアルタイムにセンサーの入力を読み取り、信号処理をしてアコースティック楽器では不可能な音を生成する、「ハイパー楽器」的にコンピューターを扱うものであったり、近年ではソースコード[^source]を書くプロセスそのものを演奏として見せるライブコーディングのような表現なども登場しており、その領域はますます広がりを見せている

[^source]:プログラミング言語で記述された、プログラムを生成するためのテキストやそのファイルデータのこと。Maxのような、テキストを用いず配線を繋いでいくようなビジュアル言語ではパッチと呼ぶこともあるが、本研究でソースコードと言ったときには音を生成するためのプログラムを記述したもの全般を指している。単にコードと略すこともある。

プログラミングに限らず音楽とコンピューターの関係性へと視野を広げてみれば、2021年現在、音楽を聴いたり、演奏したり、作ったりする上で、コンピュータが一切関与しない、という状況を考えるのは難しくなっている。作曲にはProtoolsやCubaseに代表されるDAW（Digital Audio Workstation）ソフトウェアを使用し、配信にはApple MusicやSpotifyのようなストリーミングサービスを通じて、デジタルデータという形で音楽は配布される。最終的に、コンピューターやスマートフォン上のソフトウェアでそのデータをデコードし、DAC(Digital-Analog Converter)によって電気信号へと変換され、その信号はスピーカーへと送られようやく空気の振動になり、私たちの耳へ届く。スピーカーの中にさえデジタル信号処理(DSP:Digital Signal Processing)用のチップが入っていて計算によって音質の調整をしていることも珍しくはない。2020年以後のコロナウィルスの影響も含めれば、クラシック音楽のコンサートさえもその場で空気の振動を体感することよりも録画録音されたものをコンピューターを通じて摂取することの方が多くなってしまったかもしれない。とかく音楽文化を見れば、マーク・ワイザーの提唱したユビキタス（Ubiquitous:遍在する）・コンピューティング[@Wiser1999]の概念は字義通りには達成されたようにも見える。

それにもにもかかわらず、音楽文化全体を見てみれば、音楽制作自体にコンピューターの可変性を十分に活かせるはずのプログラミングという手段を用いること自体はメインストリームとは程遠いと言える。たとえば、今日のDAWソフトウェアの中で、プログラムを用いてソフトウェアそれ自体を拡張する方法は、Ableton社のLiveにおける、音楽プログラミング環境Maxを内部拡張として用いることができるMax for Live、独自のスクリプト言語を使用できるReaperなどを除けば、VSTプラグインなど一部の仕組みに限られる。こうした拡張も、多くはC++のような、音楽を専門とする人には難易度の高いプログラミング言語で記述する必要があり、作家が自ら道具の機能を拡張するには未だハードルが高い。

音楽にプログラミングを用いることですらこの現状であるので、音楽のためのプログラミング言語や環境自体を作ることの事例はますます限られている。今日ソースコード共有サービスGitHubにおいて、「Programming Language」と検索すれば87502のリポジトリが出てくるのに対して、「Programming Language Music」では137しか出てこないことからその探究の規模の小ささががわかるだろう。実際、第3章で見ていくことになる2000年代以後に開発された音楽プログラミング言語は多く数えて30ちょっとに限られ、年を追うごとに開発者の数が増えているとも言い難い。

そして、受容の形式という視点で音楽とテクノロジーとの関わりを見てみると、どれだけ高度なテクノロジーを用いて生成された音声も、最終的には何らかの5〜10分の音声ファイルとして編集され、ほとんどの場合スピーカーやヘッドホンという2chの音波を発する装置によって発され耳に届くという、コンピューターが発明される前の19世紀の録音技術黎明期の受容の形式から大きくは変化していないと言える。

本論文での、音楽プログラミング言語を設計する第一の問題意識となるのは、このような、コンピューターが本来万能とも言ってもいい可変性を持っているはずで、しかも現状音楽に関与するあらゆるマシンの中にコンピューターが関与しているにも関わらず、音楽や音を用いた表現の形式には変化が乏しいのは何故だろうかという疑問、そして、コンピューターの可変性を十全に発揮するための道具とも言えるプログラミング言語を、音楽という目的に特化させて作ることは音楽表現の新たな可能性の追求としては一見最も素直なアプローチにも見えるのに、なぜ未だにその開発事例が少ないのか、という疑問である。

---

# 音楽のためのプログラミング言語:PLfMの指すもの

すでに音楽のためのプログラミング言語：PLfMという用語を用いたが、この語は関連研究に置いても一般的に使われる用語ではない。この語が意味するところは文字通りの意味合い以上のものはないにせよ、なぜわざわざ新しい語を用いるかについての説明をしておく必要はあるだろう。

まず、音楽のためのプログラミング言語は既存の文献では、Computer Music Language[@McCartney2002;@Mcpherson2020]、Language for Computer Music[@Dannenberg2018]、Computer Music Programming Systems[@Lazzarini2013]などといった呼ばれ方がされており、それぞれの語の使用に明確なコンセンサスがあるわけではない。その中でも敢えて筆者がComputerという語を使わない理由のひとつは、Computer Musicという語が、コンピューターを用いることで新しい音楽表現を追求する歴史的な取り組みの中にある、特定の音楽様式と結びついてしまうことを避けるためだ。既に述べたように、今日ではあらゆる音楽制作と再生のためにコンピューターが用いられている以上、あらゆる音楽が**弱い意味でのComputer Music**と呼ぶことができる。しかしそれらの多くはコンピューターでなければ不可能な、コンピューターというメディア固有の表現を行っているわけではない。同様に、たとえばFaust[@Orlarey2004]のような、信号処理のアルゴリズムを抽象化することに特化したプログラミング言語は新しい音楽表現を必ずしも目的としていないが、その技術的要素の多くはComputer Musicのための言語と共通するところがある。またPLfMという枠組みを用いることで、これまでの文献では比較対象に入れられること自体が少なかった、MML:Music Macro Languageのような、五線譜上の記法を直接的にテキストに置き換えたような、単にコンピューター上のテキストというフォーマットで音楽を表すことを目的とした言語たちも、チップチューンのような広い意味でのコンピューターを用いた音楽文化を作るための要素として議論の土台にあげることができる。

加えて、Programming EnvironmentやProgramming Systemといった語を用いない理由も説明しておこう。これは、音楽のためのプログラミング言語といった時に、たとえばMaxのような、ある特定のアプリケーションを想像するニュアンスを抑えるための選択だ。たとえば、汎用プログラミング言語の理論においては、プログラミング言語、と言った時にはその言語を実行するためのソフトウェアやプログラムのことを必ずしも指していない。たとえば同じC++という言語であったとしても、それを実行するソフトウェア（コンパイラ）はGCC、Clang、Microsoft Visual C++といったように複数存在し得るからだ。これらのコンパイラは、どれもC++の厳格な言語仕様で定まっている通りの動作をするが、言語仕様で未定義とされてる動作はそれぞれ異なるし、コンパイラが出力する実行バイナリ（≒アプリケーション）の中身は同じソースコードだったとしても異なる。音楽プログラミング言語においては、基本的にある言語＝特定のアプリケーションであることがほとんどだが、根本的にはアプリケーションの設計実装という作業とプログラミング言語の設計実装という作業は異なり、本研究が対象にしたいのは言語の設計なのだ。こうしたニュアンスを込めて筆者はEnvironmentやSystemという語を用いないことにした。極論を言えば、Faustのような厳密に意味論が定義されている言語においては、コンピューターを用いなくてもそのソースコードを手作業で解釈し実行することが可能だということを考えれば、プログラミング言語はコンピューターを使うための道具であることは間違いないにせよ、人間が直接的にバイナリを操りプログラムを構築するには限界があるという理由で開発されているという意味で、逆説的に徹頭徹尾人間のための道具でしかない。だからComputer Music Languageとも、Computer Programming Languageとも、呼ばずに、ただ音楽のためのプログラミング言語：Programming Language for Music、PLfMなのだ。

# 方法論：メディア考古学デザイン・リサーチ

本研究は、mimiumというPLfMの設計と実装を通して、音楽の制作や聴取環境においてプログラミングという手段がなぜメインストリームな手段とならないのか、音楽におけるコンピューターの利用のされ方が旧来の文化様式に固定されたままなのかの示唆を得ようというものだ。それゆえ、一見PLfMはコンピューター科学における音楽という応用分野として捉えられそうだが、本研究はその研究パラダイムの見直しも射程に入れている。

一般に音楽や、表現のためのソフトウェアやツールのデザイン、制作は、学術的研究としてはコンピューター科学の枠には入るとはいえ、その学問としての枠組みは理論物理学のような、世界を構成する要素を実験によって確かめたり、その法則を数式で記述するようなものとは大きく異なる。ある表現を支援するための道具作りには必ずその表現の様式が先立っており、数多ある表現の種類の中からその特定の表現の存在を肯定するための主張は常に恣意的なものにしかなりえないからである。この時、とくにコンピューターを用いた表現につきものである、 *新しい*表現を可能にする道具を開発するという行為を肯定するためには、まだ誰も見たことも聞いたこともなく、それを記述するための言葉も存在しないような表現の存在を認めなければならないという、記号の投機的導入が必要になってしまう。

この困難に対して、本研究ではmimiumというプログラミング言語を作ることによりあるXという表現（既存のものでは、たとえばアルゴリズミック・コンポジション、スペクトラル・プロセッシング、マイクロサウンドなど）が可能になると言った主張をせず、コンピューターを用いるユーザーが、自分自身で新しい様式や表現方法を開拓することを阻むような重力のようなものに引き寄せられているのではないか、そしてその重力の発生源を突き止めるには、表現のための道具をリバースエンジニアリングすることで（たとえ道具の構造そのものには問題がないとしても）迫れるのではないかという仮説のもとに行動することにする。そしてその時、音楽のためのプログラミング言語をリバースエンジニアリングの対象とする理由は、道具を作るための道具というメタ的存在であること、一般的な音楽を作るための楽器やソフトウェアよりも、必要な背景知識がプログラミング言語理論という音楽とは一見遠そうな分野の知識を含む分、一層複雑に見えるからだ。

このようなリバースエンジニアリングのプロセスを含め、筆者は**メディア考古学**という研究アプローチを参照している。メディア考古学とはそれ自体が明確な定義を与えられることを嫌うような性質を持っているため注意を要する用語ではあるが、ここでの定義は80年代や90年代以降のエルキ・フータモのようなメディア研究者が試みてきた、映画や映像メディアの正史には普通記述されない、万華鏡のような装置に最新テクノロジーへの熱狂の繰り返しの萌芽を見出す[@Huhtamo2015,p83][@Okubo2021,p289]ような、**歴史の中に埋没したメディアを掘り返すことで所与のものとされている歴史に別の物語を与えるアプローチ**としておこう。

メディア考古学のアプローチに存在する微妙なスペクトラムを大久保はメディア環境を形成する要因を「社会-技術」のどちらで捉えるか、学術的貢献の形として重視するのが「歴史-理論」のどちらに重きを置くかという2つの視点で整理しており、この視点はどちらもメディア考古学に共通する思想的背景となっているフーコーの『知の考古学』の解釈に大きく影響されるとしている[@Okubo2021,p285〜289]。「社会-技術」の軸では、作られたメディアテクノロジーが既存の社会的言説の影響のもとに生まれると考えるか、メディアテクノロジー自体がテクストではない形で（たとえばキットラーの例を借りれば、レコードや映画、タイプライターが）言説を形成すると考えるかという違いがある。この中でも「社会」寄りのアプローチとしては、キャロリン・マーヴィンの『古いメディアが新しかった時』に代表される、科学技術社会論（STS）の分野における社会の技術的構成（Social Construction of Technology:SCOT）という領域とも重なることは大久保も指摘しているが、SCOT的研究の中にはそれほど埋没したメディアの掘り下げといった側面を含まず、あくまでテクノロジーが社会的要請によって決定されるという、アンチ技術決定論的側面の方が大きいものも含まれる。SCOTの中で本研究と関連するものとしてはたとえばピンチとトロッコによるモーグ・シンセサイザーの歴史的記述を行った『Analog Days』[@Pinch2004]や、電子楽器用プロトコルMIDIの規格成立過程を追いかけたディドゥックの博士研究及び『Mad Skills』[@Diduck2018]のような研究が挙げられる。

一方「歴史-理論」の軸では、これまで取り上げられなかったメディア装置の一次史料の収集と記述に重きを置く、より歴史学的なアプローチか、既存の史料の中からの選択をし直すことで歴史的記述を再考することに重きを置いているとされる（もっともこれらのアプローチの違いは大久保も強調しているように、対立しているものではなく論者によって重点を置く場所が違うということで、多様なアプローチがあるメディア考古学という領域の見取り図として機能はするという程度のものだと考えた方がいい）。

メディア考古学は注目する対象が多岐にわたるためその全容を一望することは難しいが、本研究はメディア考古学の中でも音、コンピューター、インフラストラクチャという3つの要素が関わる研究であるため、ここでそれぞれの領域において行われているメディア考古学的実践について触れておく。

まず音に関してだが、メディア考古学というアプローチをこの語を用いて整理する研究は映像のような視覚メディアが中心的ではあるものの、音に関わるメディア文化史に関しても、ジョナサン・スターン『聞こえくる過去』[@Sterne2016]に代表される、サウンド・スタディーズと呼ばれる研究領域はメディア考古学と近しい性質を持っている。サウンド・スタディーズ（音研究）は現在では視覚優位のメディア文化論に対するアンチテーゼ[^visualmedia]や、音楽学に収まりきらない、音が関わる文化全般に対するカルチュラル・スタディーズや文化人類学的アプローチによる研究といった側面を持つものの、スターンが前掲書で行った音響再生産文化（Sound Reproduction Technology）としてのフォノグラフやレコードに関わる文化史の再考を「わざと思索的に語った歴史」「歴史をある種の実験室として用いている。それは、音、技術、文化に関して新しい問いを提示することを学ぶため」(ibid,p44)と表現していることが大久保の「移行期にあるメディア理論を再構築するための『実験室』『驚異の部屋』としてメディア考古学的視点が機能しているのだ」[@Okubo2021,p295]という表現と重なることからわかるように、明らかなメディア考古学的アプローチと言える。

[^visualmedia]: もっとも、音文化の研究において視覚優位なメディア文化観に対する聴覚の重要性だけを強調することは、結果的に不要な二項対立や聴覚の神秘化を引き起こしかねないものとして「視聴覚連\UTF{79B1}」とスターンが批判しているもの[@Sterne2016,p27〜34]である。

そして2つ目、コンピューターに関しては、コンピューター自体が「ニューメディア」と表現されることがあるために考古学というアプローチと一見遠い分野に見えそうな一方、計算機に関わる技術自体が驚異的な速度で、様々な隣接領域を巻き込みながら成長している分野である以上、その過去を忘却する速度や歴史的記述の多面性という意味ではコンピューター史以上にメディア考古学的実践が似合う領域もない。それゆえ、この分野では歴史的記述の長さそのものは短くとも、積み上げられてしまった技術要素を研究者自ら解体することによって、透明な背景となっている歴史や文化観を析出させるような性質が強い。古いものではフリードリヒ・キットラーのインテルCPUに搭載されたプロテクトモード批判[@Kittler1998]のような論考が挙げられる。またこうした研究はソフトウェア研究（Software Studies）と呼ばれる分野においてウエンディ・フイ・キョン・チュンが1950年代の最初機コンピューターにおけるプログラミングからソフトウェアに内在するイデオロギーについて検討したように[@Chun2001]、またアレクサンダー・ギャロウェイがTCP/IPのような基礎的プロトコルの成立過程などから新しい形の管理/制御（Control）の権力構造を議論したように[@Galloway2017]、さらに、ソフトウェアやプログラムに完結しきらない、ハードウェアとの連関を考慮するプラットフォーム研究(Platform Studies)におけるイアン・ボゴストとニック・モントフォートのアタリ製ゲーム機が生み出す映像の研究[@Bogost2009]のように、コンピューターというメディア装置の研究においてメディア考古学的省察は至る所で行われている。またこうしたソフトウェア・スタディーズやプラットフォーム・スタディーズに共通する態度としては、研究者自らがプログラミングを行うことで、高度に専門化されているコンピューティング技術やそれに関わる産業構造の批評を表層的な知識でなく実践的に行う、ブラックボックスを開く態度という特徴がある。このことはソースコードそのものを批評的に読み解くクリティカル・コード・スタディーズという研究を行うマーク・C・マリノによるキットラーがソフトウェア研究の過程で残したソースコードの検討[@Marino2001]や、キットラーの研究を行う梅田拓也による、キットラーのアナログシンセサイザー制作経験を彼のプロテクト・モード論考の背景として検討したもの[@Umeda2021]などに見ることができる。

本研究で特に着目するのは（第3章で詳しく検討するが）アラン・ケイとアデル・ゴールドバーグが提示したメタメディアとしてのコンピューターに対する歴史的位置づけと評価である。レフ・マノヴィッチは『ニューメディアの言語』[@Manovich2001]において映画との比較という、これもある意味での考古学的検証においてコンピューターのメディア固有性について検討したが、続く『Software Takes Command』ではコンピューターが新しいメディウム自体を自分自身で生み出せるメタメディアであることにその特徴をより強調し、その原点としてケイとゴールドバーグのDynabookという装置をおいた[@Manovich2013]。一方で、コロラド大学ボルダー校においてMedia Archaeology Labを主宰するロリ・エマーソンは具体詩（コンクリート・ポエトリー）とコンピューターを用いた視覚表現を行うアーティストの歴史的接点として、ケイとゴールドバーグのメタメディアとしてのコンピューターの思想を歴史的原点に位置付けるが、それはマノヴィッチと対照的に、現代のパーソナルコンピューティング環境がメタメディアの不完全な形で社会実装であり、アクセス不可能な装置となってしまった失敗の歴史として位置付けている[@Emerson2014]。本研究はエマーソンの立場に近い態度で、音楽ソフトウェアという異なる領域からやはりDynabookのようなメタメディアとしてのコンピューターの思想を検討することになるが、この立場におけるメディア考古学としてのコンピューター史は、映像や音響メディア史において歴史に記述されることの少なかったメディア装置を掘り返すこととは異なり、ケイとゴールドバーグのようにある種の正当な歴史においても原点として位置付けられている活動を、むしろ失敗した試みとして書き換える試みである。これは「歴史-理論」の軸でいえば既存の歴史に置かれている要素をあえて読み替える「理論」側に寄った位置づけであり、より厄介で注意を要するものだが、本研究における音楽プログラミング言語の制作の一体どこがメディア考古学的なのかという質問への回答は、エマーソンと同じく**歴史を辿ることで現代のコンピューター環境を、万能メディア装置のなり損ないと位置付ける**ことにあると言えるだろう。

3つ目にインフラストラクチャという視点におけるメディア考古学的アプローチという立場だ。ここで筆者が言うインフラストラクチャとは主にISOやANSI、JISで定義されるような標準規格（Standard）やフォーマットのことを意味しており、補集合的な補足をすれば、装置でもなく、アルゴリズムでもなく、コンピュータープログラムでもないが社会や文化に大きな影響を与えているもの、という表現ができるだろう。このインフラストラクチャへの注目の大きな背景としては、科学技術社会論における研究対象が、社会に大きくインパクトを与えた革新的研究（イノベーション）ではなく、すでに社会に浸透してしまったテクノロジーに注目するという反動を起こしたことが挙げられる。ふだん不可視のインフラストラクチャに着目することで知の伝播や政治的権力関係のかたちを明らかにするというアプローチを、ボウカーは「インフラ的転倒(Infrastructural Inversion)」[^inversion][@Star2001,p34]と呼んだが、このインフラの分析においてその成立過程の記述のような通時的分析が多く含まれればそれはメディア考古学的アプローチと多く共通するところがある。これは既に挙げたギャロウェイのプロトコル概念の分析も含まれるし、スターンが『聞こえくる過去』の後に『MP3』で提示したフォーマット理論[@Sterne2012]の概念と大きく共通する。またボウカーはインフラ的転倒の代表例としてベッカーの『アート・ワールド』[@Becker2019]のような、芸術を、それを支える美術館や経済システム、特定の集団の方に着目することで、 「アート作品を生み出す社会分業こそが、それに固有の作品を生産する」（ibid、p423訳者解説）という視点の転換を例に挙げているが、これは音楽という領域で検討すれば、スモールの『ミュージッキング』[@Small2009]のように、ある文化を構成する社会的集団を、たとえば音楽であれば作曲家や演奏家、聴衆だけではなくコンサートのスタッフや楽器製作者も含めることでよりその権力関係や文化のあるべき姿の議論の焦点を合わせやすくするアプローチとも捉えられる。実際スターンはスモールの議論を延長し、「音楽産業など存在しない」というエッセイで、音楽ソフトウェアの開発者が音楽文化を構成する一員として捉えられることが少ないことの不自然さを指摘している[@Sterne2017]。本研究においても、Computer Music Languageという、ある種独立して捉えられてきたソフトウェア群の歴史を、コンピューターを用いている音楽の中におけるソフトウェアというより広い枠組みのなかで編み直すことを目標としており、かつそうした音楽ソフトウェアやプログラミング言語は、それらを用いて作られた音楽だけを事後的に分析する上では不可視なインフラストラクチャと言える点で、これらの研究と問題意識を共有している。

[^inversion]: 「インフラ的転倒」という訳は[@Fukushima2017]に倣っている。

また最後に、芸術実践としてのメディア考古学的アプローチという要素も本研究と接する部分であることを説明する必要がある。フータモが岩井俊雄やポール・デマリーニスのような芸術家の取り組みをメディア考古学的実践のひとつとして位置付けていたり[@Huhtamo2015,7章]、パリッカとハーツがサーキット・ベンディングという電子回路を意図的に壊すことで楽器として用いるアプローチを同様に分析している[@Parikka2014]ように、メディア装置自体を作る、あるいは既存のメディア装置の用途をねじ曲げるような芸術実践は後付け的にメディア考古学的と評されることもある。近年ではこれを作品製作の方法論として自ら用いる（これを**メディア考古学的制作**と呼ぼう）ものが、たとえば情報科学芸術大学院大学（IAMAS）において城一裕が中心となって活動した『車輪の再発明』プロジェクト[@Jo2016]や、Human-Computer Interactionの分野から派生した音楽表現のための新しいインターフェースの会議（New Interface for Musical Expression:NIME）におけるレプリの『Cembalo Scrivano』[@Lepri2018]などのように現れてきている。何より筆者自身も意図的に音響遅延線メモリーのような使われなくなった装置を再構築することで、デジタルデータの身体性を再考するサウンドインスタレーション作品『遅れ/送れ | post/past』[@Matsuura2016]を製作してきたように、そのバックグラウンドはコンピューター科学でもメディア研究でもなく、音を用いた芸術作品制作にあり、そのための方法論としてメディア考古学を用いてきていたということを表明しておくべきだろう。なぜならメディア考古学を制作の方法論として自覚的に用いるということは、単にこれまで描かれることのなかった歴史を描くのみならず、その先頭に自らが作った作品を配置することでその歴史の先に進むべき方向を表明する政治的態度が多分に含まれるという点において、第三者にメディア考古学的アプローチと位置付けられた作品と異なるからだ。その点では、城が背景に挙げるように過去の事象を探索し、ありえたかもしれない現在や、ありうるかもしれない未来（Alternative Presents & Speculative Futures）について思索し議論を引き起こすことを目的としたデザイン・フィクション[@Auger2010]やスペキュラティブ・デザイン[@Raby2013]といった概念との共通点が見出せるだろう。オージャーによれば[@fig:auger]の通り、デザイン・フィクションには大きく分けて現在発展しつつあるテクノロジーが普及した先にある社会像について検討することで「文化のリトマス試験紙」的な役割を果たすことを目指す「Speculative Futures」と、一方で現在のテクノロジーを異なるイデオロギーや組み合わせで用いることで、「我々の現状がなぜこうなのか」を問いかけ直す「Alternative Presents」という2種類の方向があるとしている。メディア考古学的制作は過去の歴史を編み直すという部分でAlternative Presentsの方に近いと言えるが、さらに少し先の未来についても問いかける点でSpeculative Futuresの要素も持ち合わせている。ともあれ、本研究はプログラミング言語を作るという作業を中心に置く以上、メディア考古学という歴史の再組織化を中心においた方法論だけでは研究としての位置づけは片手落ちといったところだろう。そのため、本研究における実際の制作に関してはこうしたデザインにおける運動の中に位置付けることで補完することにする（これは2章で詳しく議論する）。

![[@Auger2010]より、Alternative PresentとSpeculative Futuresの概念を表した図。](img/auger_alternativepresent.png){#fig:auger width=100%}

# mimium制作の目標設定

メディア考古学とデザインという背景をもとにしていることで、mimiumの設計と開発は学術的研究としては次の3つのような特徴を持っている。

**1:まず、研究のアウトプットのひとつであるプログラミング言語、mimiumの設計や実装はプロトタイプではなく、実際に使われることを想定している。**

なぜなら、音楽プログラミング言語がなぜ多くは作られていないのかという疑問に答えるには、その言語の機関部分だけを作るーつまり、Proof-of-Work的なプロトタイプを作るだけでは、たとえば実際にソースコード共有サイトへのアップロード、リリースの作業、さらにリリース後のメンテナンスや、ドキュメンテーションといった、ツールを実際に運用するプロセスの中にも、言語を実際に作るにあたって高いハードルが存在しているかもしれなからだ。実際に、mimiumの実行プログラムのソースコードはすでにGithubに公開されており、何人かが開発の一部に参加してくれてもいる。
<!-- また音楽向けの言語はオリジナルの開発者が中心的役割になって継続的開発、運用を続けているケースが多数を占める。代表的な例としてはPuredataを開発したMiller Pucketteは今日まで30年近く開発とメンテナンスを続けている。数少ない例外としてはオリジナルの作者が早期に開発から抜け、コミュニティベースで運用を行っているSuperColliderや、Cycling'74という企業によってメンテナンスされるMaxといった例を挙げることができる。 -->

**2:しかし、研究のアウトプットとしてのプログラムで実用的に役に立つほどに完成はしていなくてもよいものとする。**

LISPというプログラミング言語のプログラマーで『ハッカーと画家』というエッセイ集を書いたポール・グレアムはプログラミング言語が常に完成しないという特徴を次のように表現している。

> また、プログラミング言語はまず、 完成されたプログラムの形ではなく、 プログラムがまさに開発されている最中の形をとるということを忘れないで欲しい。 芸術の分野で仕事をしている人なら誰でも、その二つの過程には 異なる媒体が必要になるだろうと言うだろう。 例えば、大理石は最終的な考えを保持するには素晴らしく長持ちする媒体だが、 新しい考えを発展させている時にはおそろしく融通の利かない媒体でもある。

> （中略）われわれはつい、 完成したプログラムがどれだけ良く見えるかで言語の良さを測ってしまいがちだ。 二つの言語で書かれた同じプログラムを眺めて、 片方がもう片方よりうんと短かかったりすると、その議論にはひどく説得力がある。 だが芸術の方向からこの問題に取り組んでみれば、 そういう測り方をしてしまうことは少ないだろう。 プログラミング言語を、大理石のような、完成形は美しいけれど それを使った製作が苦痛であるような媒体にはしたくはないだろう。[@Graham2003](http://practical-scheme.net/trans/desres-j.html)

この文章にはプログラミング言語自体の評価の難しさに、「そのプログラミング言語で書かれたソースコードの読みやすさや簡潔さ」や「そのプログラミング言語でプログラミングをする時のユーザー体験」や、さらには「そのプログラミング言語自体を開発する過程の困難さ」といったことまでを含める必要があると提起しているように読める。

実際のところ、LISPに限らずプログラミング言語やそれを実行するプログラムには明確な完成という状態を定義しにくい。常に新しい言語仕様が追加されたり削除されたりを繰り返しながら時間をかけてアップデートされていく。同じC++という言語でも、C++98という初期バージョンの言語とC++20という最新の仕様では、言語仕様もそれで書かれるソースコードの様式もほとんど別の言語と言ってもいいほどに大きく異なる。

さらに、プログラミング言語の開発やそれが実際に使われるようになるまでには一般的に2年を超える長い時間がかかるため、実用になって初めてその内容を研究として提示するプロセスを取ってしまっては研究サイクルとして時間が掛かりすぎるという問題がある。たとえばRubyを開発したまつもとゆきひろによればRubyの開発自体は1993年に成され、最低限の機能が揃ったのは半年後[@Matsumoto2014,51p]ながら、最初に公開されたバージョンである0.95は1995年と2年の時間を要している。音楽系の言語の例で言えば、mimiumの参考になっている言語であるFaustはプロジェクト自体が始まったのが2002年(https://faust.grame.fr/about/)だが、最初にリリースされた正式なバージョン0.9.0はやはり2年後の2004年になってリリースされている（https://github.com/grame-cncm/faust/tree/v0-9-0）。

それでも研究対象としては具体的な幾つかの言語仕様に焦点を当てて議論を行うことで学術的な知見を生み出すことは十分に可能だと言えるはずだ。実際にmimiumは最初のバージョンをリリースするのに9ヶ月、そもそも音楽のための言語でありながら信号処理をして実際に音がなるまでに7ヶ月の時間を要しており、この論文が書かれている現在(バージョン0.4.0)でも、外部ファイルを読み込むinclude機能は単なるテキスト置換で行っており、実行性能の効率も悪いし予期しない動作を引き起こしかねないという、とりあえずの間に合わせとして実装されているように、暫定的な機能やバグが多数存在する。

**3:学術的研究として、作った言語の評価としてユーザーからのフィードバックを（定量的な実験結果であれ、インタビュー等の質的な内容であれ）必ずしも必要としない。**

これはコンピューター科学の研究として考えると一見異質に思えるかもしれないが、その理由としては、筆者が焦点を当てたいのは音楽プログラミング言語がなぜ使われないかよりも、なぜ作る人の人数が増えないのかという問題であること、さらには、プログラミングという行為は、誰かの作ったライブラリのソースコードが公開されてさえいれば、その中身をどこまでも辿っていける、知識の階層を思うがままに辿っていける道路のネットワークであるにもかかわらず、コンピューターの中で音を（アプリケーションなどを通して）扱うことと、音楽や音のためのプログラムを作ること、さらには音楽や音を**記述するためのプログラム**：音楽プログラミング言語を作るということにはそれぞれ大きな隔たりがある、という問題であるからだ。この疑問に答えるために調べなければいけない対象は、すでに多く研究対象となっているユーザー：音楽のためのプログラム、アプリケーションや音楽プログラミング言語を仕様する人たちだけではなく、むしろ研究主体である自分自身とその経験なのだ。つまり音楽プログラミング言語やそれを作るという行為がブラックボックス化されている現状を、自らの手で作ることによって開き、そこで使われる知識や語彙の体系化を改めて試みることで疑問に対するヒントを掴むような道筋を辿ることになる。

もちろんこれは、1.で述べたように実用的なツールとしてもmimiumを開発している以上、そのツールをよりよいものにしていくために今後ユーザーにインタビューなどの形でフィードバックを求めること自体は有益になるだろう、という意見を否定するものにはならない。

まとめると、本研究は、何か既存の言語に足りない機能があったり、既存の言語ではできない表現があるので新しい言語を作るのではなく、言語の実装と文献調査を通して、音楽プログラミング言語という研究領域はどういった領域か、またその領域にどんな課題があるかといったものを明確化することを主眼においている。いわば、音楽のためのプログラミング言語という、コンピュータ科学や音楽全体からすれば応用分野である領域において基礎研究を行おうとしている。そのため、プログラミング言語mimium自体も特定の問題意識や仮説に基づいた設計や実装が行われてはいるものの、実装するうちにその問題意識も徐々に変化していることには留意する必要がある。第2~4章におけるPLfMの歴史的背景と第5章で議論するPLfMの存在論はmimium実装のためのモチベーションであると同時に、mimiumを実装することによって得られたリサーチ・アウトプットでもある。

このような考察→設計→実装→考察…といった循環的な作業を行う以上、それを問題提起→解決という線状のプロセスに形式的にでも開くことは、試行と実験を繰り返す中で発生する考えの変遷のディテールを削いでしまうことは否定できない。そこで、それを補うためにもmimiumの設計と実装が時系列的にどのように行われてきたかについてをまず簡単にまとめておくことにする。
