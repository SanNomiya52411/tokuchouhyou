<template>
	<p>特徴: {{ feature }}</p>
	<p>項番: {{dice1}}-{{dice2}}</p>
	<p>特徴効果: {{featureEffect}}</p>
	<button @click="random">Dice</button>
</template>

<script>
export default {
	data() {
		return {
			feature: 'Diceボタンを押してね！',
			featureEffect: 'Diceボタンを押してね！',
			dice1: 0,
			dice2: 0
		}
	},
	emits:[],
	methods: {
		random(){
			this.dice1 = Math.floor(Math.random() * (6 + 1 - 1)) + 1
			this.dice2 = Math.floor(Math.random() * (10 + 1 - 1)) + 1
			this.$emit('featureNumber',this.dice1,this.dice2)
			if(this.dice1 === 1){
				switch(this.dice2){
					case 1:
						this.feature = '風邪を引かない'
						this.featureEffect = '君は難しいことなど考えず、元気いっぱいに育った。INT-1、CON+2'
						break
					case 2:
						this.feature = '大きな体'
						this.featureEffect = '生まれつき大きな体に恵まれている。SIZ+1'
						break
					case 3:
						this.feature = '素早い'
						this.featureEffect = '柔軟さと軽快さを併せ持っている。DEX+1。\r\nただし、SIZが9以下の場合は素早い上に小柄であるため、DEX+2'
						break
					case 4:
						this.feature = 'オシャレ'
						this.featureEffect = 'いつも身だしなみに気を使っている。APP+1'
						break
					case 5:
						this.feature = '天才'
						this.featureEffect = '生まれつき頭の回転が早い。INT+1'
						break
					case 6:
						this.feature = '強固な意志'
						this.featureEffect = '何事にも動じない、強靭な精神の持ち主だ。\r\nPOWおよびSANは変動しないが、現在正気度ポイントに+5'
						break
					case 7:
						this.feature = '勉強家'
						this.featureEffect = 'あなたは日々学ぶことに精進している。EDU+1。また、EDUによる年齢の下限は適用されない'
						break
					case 8:
						this.feature = '幸運のお守り'
						this.featureEffect = '幸運のお守り(KPと相談した物品)を持っている。身に着けている限りPOW+1。\r\nもし手放したり紛失すれば不運を招きPOW-1。POWの変化により＜幸運＞は変化するが、正気度ポイントは変化しない。'
						break
					case 9:
						this.feature = '一族伝来の宝物'
						this.featureEffect = '画、書物、武器、家具などの個人的な宝物で、探索者やCPにとって特別な価値を持つ品を所有している。\r\n宝物は、魔術的な価値を持つAFかもしれない。'
						break
					case 10:
						this.feature = '予期せぬ協力者'
						this.featureEffect = '探索者には、いかなる理由か自分に忠誠を尽し、援助に来るかもしれない協力者がいる。\r\nKPが協力者の正体を決める。また、協力者の影響力を1D100ロールで決める(数字が大きいほど影響力が高い)。'
						break
					
				}
			}else if(this.dice1 === 2){
				switch(this.dice2){
					case 1:
						this.feature = '手先が器用'
						this.featureEffect = '任意の＜製作＞1つの基本成功率が50%となる(PLは分野を決めること)。\r\nさらに＜機械修理＞および＜電気修理＞に+10%'
						break
					case 2:
						this.feature = '影が薄い'
						this.featureEffect = '生まれつき目立たない。＜忍び歩き＞および＜隠れる＞に+20%'
						break
					case 3:
						this.feature = '親の七光り'
						this.featureEffect = '名家の出身、または親が有名人かもしれない。＜信用＞に+20%'
						break
					case 4:
						this.feature = '愛書家'
						this.featureEffect = 'あらゆるジャンルの蔵書を持っている。\r\n＜図書館＞に+20%。さらに図書館へ出掛けなくても、自宅の書庫で＜図書館＞ロールが可能になる。'
						break
					case 5:
						this.feature = '鋭い洞察力'
						this.featureEffect = '優れた感覚の持ち主であるため＜目星＞に+30%'
						break
					case 6:
						this.feature = 'アウトドア派'
						this.featureEffect = '暇さえあれば季節を問わず、野外活動に繰り出している。＜ナビゲート＞、＜博物学＞、＜追跡＞にそれぞれ+20%'
						break
					case 7:
						this.feature = '珍しい技能'
						this.featureEffect = '日常生活では役立たないが、特定の人を感心させるような[INT×5]%の技能を1つ、KPと相談したうえで持つことができる。\r\n例→＜製作（プラモデル）＞、＜芸術（対戦格闘ゲーム）＞、＜他言語（インターネットスラング）＞など'
						break
					case 8:
						this.feature = '芸術的才能'
						this.featureEffect = '稽古事を幼い頃に習っていたか、実用ブログなどで人気を博している。\r\n任意の＜芸術＞1つに[INT×3]%を加える。PLは音楽、著述などの専門分野を指定すること。'
						break
					case 9:
						this.feature = 'バイリンガル'
						this.featureEffect = '日本以外の国で生活したことがある。\r\n[EDU×5]%を、最大3つまでの＜他の言語＞に割り振ることができる。'
						break
					case 10:
						this.feature = '前職'
						this.featureEffect = '以前別の職に就いていたか、幼少期に何か得難い体験をしている。\r\n[EDU×3]%を前職としてPLが決めた、職業上の技能に割り振ることができる。'
						break
					
				}
			}else if(this.dice1 === 3){
				switch(this.dice2){
					case 1:
						this.feature = '天気予報'
						this.featureEffect = '外を見て＜アイデア＞ロールに成功すれば、短い期間([1D6+1]時間)の正確な天気を予想できる。\r\n降水確率や風の向き・強さ、嵐の時間帯、雷の落下しやすい場所なども予測可能だ。'
						break
					case 2:
						this.feature = 'プロ・ドライバー'
						this.featureEffect = '小さい頃から乗り物で遊んでいた。あらゆる＜運転＞技能の基本成功率が50%となる。'
						break
					case 3:
						this.feature = '飛ばし屋'
						this.featureEffect = '空間把握能力に優れている。あらゆる＜操縦＞技能の基本成功率が50%となる。'
						break
					case 4:
						this.feature = '戦士'
						this.featureEffect = '周囲の物は全て武器だと考えている。\r\nあらゆる＜近接戦闘武器(肉体を使った技能は除く)＞技能の基本成功率が50%となる。'
						break
					case 5:
						this.feature = '重火器の達人'
						this.featureEffect = '銃火器と何かの縁があり、普段から親しんでいる。\r\n火器技能5つ(HG、SMG、SG、MG、AR)の基本成功率が50%となる。'
						break
					case 6:
						this.feature = '格闘センスの持ち主'
						this.featureEffect = '幼い時から道場で鍛えられてきた。\r\n素手の戦闘技能3つ(＜キック＞、＜組みつき＞、＜頭突き＞)の基本成功率が50%となる。'
						break
					case 7:
						this.feature = '俊敏'
						this.featureEffect = 'どんな時でも鋭く素早く状況を把握できる。\r\n＜回避＞の基本成功率が[DEX×2]ではなく[DEX×5]となる。'
						break
					case 8:
						this.feature = '信頼のおける人'
						this.featureEffect = '探索者は自分の家族や友人などの仲間を粗末にしたりせず、可能な限り助けようとする人間だ。\r\nその評判が今後も続く限り、任意のコミュニケーション系技能3つにそれぞれ+10%。'
						break
					case 9:
						this.feature = 'スポーツ万能'
						this.featureEffect = '1つの技能に+20%、3つの技能に+10%、合計4つの運動系技能にボーナスを加える。'
						break
					case 10:
						this.feature = '平凡な容姿'
						this.featureEffect = '平凡な顔立ちなため、他人の印象に残りにくい。\r\n＜変装＞に+20%。加えて、1度しか会ったことのない相手ならば、相手が＜アイデア＞ロールに失敗すれば、「よくある顔です」と言い訳するだけで、別人としてごまかせる。'
						break
					
				}
			}else if(this.dice1 === 4){
				switch(this.dice2){
					case 1:
						this.feature = '目つきが悪い(D)'
						this.featureEffect = '目つきが悪すぎて、知り合い以外から怖がられる。APP-1。さらに＜信用＞-10%'
						break
					case 2:
						this.feature = '方向音痴(D)'
						this.featureEffect = '＜ナビゲート＞の基本成功率が1%となる。加えて、経験ロールで成長することができない。'
						break
					case 3:
						this.feature = '異性が苦手(D)'
						this.featureEffect = 'どうしても異性とうまく話ができない。異性に対する交渉技能は-10%'
						break
					case 4:
						this.feature = '動物に嫌われる(D)'
						this.featureEffect = '独特の佇まいのせいで、たいていの動物は探索者を見るなり威嚇してくる。'
						break
					case 5:
						this.feature = '不思議ちゃん(D)'
						this.featureEffect = '時折突拍子もない言動で周囲を騒がせることがある。\r\n別の世界から来た精神交換者か、妄想が生み出した人格がしばしば表面に出ているのかもしれない。'
						break
					case 6:
						this.feature = '寄せ餌(D)'
						this.featureEffect = '人間以外の怪物に好かれやすい。誘拐されれば殺されずに監禁されるか、もっとひどい目に遭うこともある。'
						break
					case 7:
						this.feature = '眼鏡をかけている(D)'
						this.featureEffect = 'あなたは常時眼鏡を必要とする視力だ。眼鏡を失えば、視覚に関連する技能は-20%となる。'
						break
					case 8:
						this.feature = '大切なもの(D)'
						this.featureEffect = '他人には価値のないものだが、大切な品物をいつも身に着けている。失った時、1/1D8の正気度ポイントを失う。'
						break
					case 9:
						this.feature = '暗黒の祖先(D)'
						this.featureEffect = '邪悪な一族、カルティスト、人肉嗜食者、もしくは超自然のクリーチャーの子孫である。\r\nD100をロールし、結果が大きいほど、より邪悪な存在となる。'
						break
					case 10:
						this.feature = '夜に弱い(D)'
						this.featureEffect = '夜には、すぐ眠くなる体質である。\r\n深夜0時を過ぎても活動しようとすれば、＜アイデア＞および＜知識＞ロールの成功範囲が1/2(端数切り上げ)となる。ただし、早起きは得意である。'
						break
					
				}
			}else if(this.dice1 === 5){
				switch(this.dice2){
					case 1:
						this.feature = '動物に好かれる'
						this.featureEffect = '独特の佇まいのおかげか、たいていの動物がなついてくる。'
						break
					case 2:
						this.feature = '斜め上からの発想'
						this.featureEffect = '狂気に陥った場合、独特の感性により、原因となった恐怖に対して秘められた真実を見抜くことができる。\r\nKPはクライマックスで宇宙的恐怖の一端を教えてくれるだろう。ただし、クライマックス以外の場面では、何も教えてくれない可能性がある。'
						break
					case 3:
						this.feature = '失敗は発明の母'
						this.featureEffect = 'あなたは失敗から学ぶことを信条としている。技能ロールに「96」以上の目を出して「失敗」した際、ただちに特別な成長ロールを行う。\r\n失敗すれば0ポイント、成功すれば1ポイントの技能ポイントを得る。'
						break
					case 4:
						this.feature = 'ペット'
						this.featureEffect = '探索者には最愛の犬、猫、鳥などがいる。シナリオとシナリオの間、一緒に触れ合うことで、正気度ポイントを1D3ポイント増加させてもよい。\r\nただし増加する上限は、能力値SANあるいは最大正気度ポイント(99-＜クトゥルフ神話＞)のうち、どちらか低いほうになる。'
						break
					case 5:
						this.feature = 'おおらか'
						this.featureEffect = '嫌なことをすぐに忘れられる。精神科クリニックや療養所などで正気度ポイントの回復が+1増加する。'
						break
					case 6:
						this.feature = '異物への耐性'
						this.featureEffect = '体内の免疫力が発達している。毒(POT)を抵抗表で競う際に、成功の範囲に+20%'
						break
					case 7:
						this.feature = '潜水の名人'
						this.featureEffect = '長時間息を止めていられる。窒息に対するCONロールの成功範囲に+20%'
						break
					case 8:
						this.feature = '大酒飲み'
						this.featureEffect = '体内の免疫力が発達している。毒(POT)を抵抗表で競う際に、成功の範囲に+20%。あなたは酒にめっぽう強く、酔いにくい。\r\nアルコールを毒のように扱う場合、探索者は全てのアルコール関連のPOTを1/2(端数切り上げ)にする。'
						break
					case 9:
						this.feature = 'ど根性'
						this.featureEffect = '根性がある。あらゆる抵抗表を使用したロールで、成功する範囲に+5%'
						break
					case 10:
						this.feature = '受け身'
						this.featureEffect = 'どんなときでも、きちんと受け身を取って被害を最小限に抑えることができる。ショックロールの成功の範囲に+20%'
						break
					
				}
			}else if(this.dice1 === 6){
				switch(this.dice2){
					case 1:
						this.feature = '奇妙な幸運'
						this.featureEffect = 'クトゥルフ神話の神性や怪物がランダムに目標を攻撃する際、その対象からは除外される。\r\nただし単独で攻撃される場合や範囲攻撃の中にいた場合は、対象となる'
						break
					case 2:
						this.feature = '投擲の才能'
						this.featureEffect = '＜投擲＞で投げることのできる武器のダメージ・ボーナスは1/2ではなく、通常のダメージ・ボーナスとなる。'
						break
					case 3:
						this.feature = '鋼の筋力'
						this.featureEffect = 'ダメージ・ボーナスが1段階向上する(「-1D4」なら「+0」に。「+0」なら「+1D4に」)。\r\nただしダメージ・ボーナスが「1D6」以上ある場合は、1段階向上する代わりにダメージ・ボーナスにさらに+1'
						break
					case 4:
						this.feature = '実は生きていた'
						this.featureEffect = '生き残るすべに長けている。死からの生還のチャンスが通常の次ラウンド以内ではなく、5ラウンド以内に伸びる。'
						break
					case 5:
						this.feature = '急所を見抜く'
						this.featureEffect = '狩人の素質を持っている。貫通の確率は、通常の1/5ではなく、1/2となる。ただし最大40%である。'
						break
					case 6:
						this.feature = '急速な回復力'
						this.featureEffect = 'あなたは新陳代謝に優れている。耐久力を回復するロールの結果に+1。'
						break
					case 7:
						this.feature = '不屈の精神力'
						this.featureEffect = '気絶しても、次の各ラウンドの最初に[CON×2]ロールを行う。\r\n成功なら治療を受けずとも自分から目覚めて、そのラウンドから再び行動が可能となる。'
						break
					case 8:
						this.feature = 'マニア・コレクター'
						this.featureEffect = 'コイン、本、昆虫、芸術、宝石、歴史的な遺物などを収集している。任意のコレクションを1つ決定すること。\r\nその筋では有名人であり、＜幸運＞ロールに成功すれば相手にも共感を得られて、感動を与えられるかもしれない。'
						break
					case 9:
						this.feature = '行方不明の家族'
						this.featureEffect = '探索者には行方不明の家族がおり、キャンペーンの間に現れるかもしれない。'
						break
					case 10:
						this.feature = '好意を寄せられている'
						this.featureEffect = 'シナリオに登場する誰かに好意を持たれる。KPの裁量で誰が、なぜ好きなのかを決定する。\r\nどれほど好意を寄せているかはD100ロールで決める(数字が大きいほど好き)。'
						break
					
				}
			}
		}
	},
}
</script>

<style scoped>
	p{
		border-bottom: 1px solid red;
	} 
	button {
		font-size:30px;
	}
</style>
