<template>
  <div class="Main">
    <Header />
    <div class="Contents">
      <div class="Section Section--lower" id="archives">
        <h1 class="Heading Heading--center">
          <span class="Heading__subtitle">Archives</span>実績一覧
        </h1>
        <div>
          <div class="Box">
            <h2 class="Box__title">経歴別で絞り込む</h2>
            <div class="Box__row">
              <div class="Radio__wrap">
                <input class="Radio" type="radio" name="checkedCareer" value="nishimura" v-model="checkedCareer" id="cat_nishimura">
                <label class="Radio__label" for="cat_nishimura">
                  <span class="Radio__text">
                    株式会社 西村<span class="Radio__date">2020/10～</span>
                  </span>
                </label>
              </div>
              <div class="Radio__wrap">
                <input class="Radio" type="radio" name="checkedCareer" value="phonogram" v-model="checkedCareer" id="cat_phonogram">
                <label class="Radio__label" for="cat_phonogram">
                  <span class="Radio__text">
                    株式会社 フォノグラム<span class="Radio__date">2016/12～2020/10</span>
                  </span>
                </label>
              </div>
            </div>
            <h2 class="Box__title" v-if="checkedCareer == 'phonogram' || checkedCareer == 'nishimura'">カテゴリ別で絞り込む</h2>
            <div class="Box__row" v-if="checkedCareer == 'phonogram' || checkedCareer == 'nishimura'">
              <div class="Box__checkboxWrap" v-if="checkedCareer == 'phonogram'">
                <input class="Checkbox" type="checkbox" name="checkedCategory" value="Corporate" v-model="checkedCategory" id="cat_corporate">
                <label class="Checkbox__label" for="cat_corporate">Corporate</label>
                <input class="Checkbox" type="checkbox" name="checkedCategory" value="Recruit" v-model="checkedCategory" id="cat_recruit">
                <label class="Checkbox__label" for="cat_recruit">Recruit</label>
                <input class="Checkbox" type="checkbox" name="checkedCategory" value="Service" v-model="checkedCategory" id="cat_service">
                <label class="Checkbox__label" for="cat_service">Service</label>
                <input class="Checkbox" type="checkbox" name="checkedCategory" value="Security" v-model="checkedCategory" id="cat_security">
                <label class="Checkbox__label" for="cat_security">Security</label>
                <input class="Checkbox" type="checkbox" name="checkedCategory" value="CRM" v-model="checkedCategory" id="cat_crm">
                <label class="Checkbox__label" for="cat_crm">CRM</label>
                <input class="Checkbox" type="checkbox" name="checkedCategory" value="Brand" v-model="checkedCategory" id="cat_brand">
                <label class="Checkbox__label" for="cat_brand">Brand</label>
                <input class="Checkbox" type="checkbox" name="checkedCategory" value="Vuejs" v-model="checkedCategory" id="cat_vue">
                <label class="Checkbox__label" for="cat_vue">Vue.js</label>

                <input class="Checkbox" type="checkbox" name="checkedCategory" value="SPA" v-model="checkedCategory" id="cat_spa">
                <label class="Checkbox__label" for="cat_spa">SPA</label>
                <input class="Checkbox" type="checkbox" name="checkedCategory" value="Angular" v-model="checkedCategory" id="cat_angular">
                <label class="Checkbox__label" for="cat_angular">Angular</label>
                <input class="Checkbox" type="checkbox" name="checkedCategory" value="Wordpress" v-model="checkedCategory" id="cat_wordpress">
                <label class="Checkbox__label" for="cat_wordpress">Wordpress</label>
                <input class="Checkbox" type="checkbox" name="checkedCategory" value="BoltCMS" v-model="checkedCategory" id="cat_bolt">
                <label class="Checkbox__label" for="cat_bolt">Bolt CMS</label>
                <input class="Checkbox" type="checkbox" name="checkedCategory" value="MovableType" v-model="checkedCategory" id="cat_mt">
                <label class="Checkbox__label" for="cat_mt">MovableType</label>
              </div>

              <div class="Box__checkboxWrap" v-if="checkedCareer == 'nishimura'">
                <input class="Checkbox" type="checkbox" name="checkedCategory" value="UX" v-model="checkedCategory" id="cat_ux">
                <label class="Checkbox__label" for="cat_ux">UX</label>
                <input class="Checkbox" type="checkbox" name="checkedCategory" value="UI" v-model="checkedCategory" id="cat_ui">
                <label class="Checkbox__label" for="cat_ui">UI</label>
                <input class="Checkbox" type="checkbox" name="checkedCategory" value="Design" v-model="checkedCategory" id="cat_design">
                <label class="Checkbox__label" for="cat_design">Design</label>
              </div>
            </div>
          </div>

          <ul class="Card">
            <li class="Card__item" v-for="item in matched" :key="item.id" @click="move(item.id)">
              <img :src="item.imgSrc" alt="">
              <div class="Card__body">
                <div class="Card__modules">
                  <span class="Card__date">{{ item.date }}</span><br>
                  <span v-for="i in item.category" :key="i" :class="'Label Label--' + i " >{{ i }}</span>
                </div>
                <h2 class="Card__title">{{ item.title }}</h2>
                <p class="Card__subtitle">{{ item.subtitle }}</p>
              </div>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>

</template>

<style lang="scss" scoped>
  @import "../../assets/sass/pages/archives.scss";
</style>

<script>
  export default {
    name: 'Parent',
    data: () => {
      return {
        postItem: "",
        checkedCareer: '',
        checkedCategory: [],
        articleType: null,
        items: [
          {
            id: 1,
            date: "2021/11~",
            title: "かき小屋 宇品店",
            type: "nishimura", // nishimura, phonogram, personal
            articleType: 1,
            category: ["UX","Design"],
            subtitle: "穴場観光地のUXリサーチ＆webサイトリニューアル",
            overview01: "かき小屋宇品店は広島県の実証事業である「瀬戸内 海の道構想」を基に、気軽に・手軽に牡蠣を食べることができる場所（通称：かき小屋）の提供を行っている「ひろしまオイスターロード」の系列店のうちの1店舗です。",
            overview02: "今回、webサイトリニューアルにあたり、UX領域では定量調査・定性調査の可視化からペルソナとカスタマージャーニーマップの作成、それらに基づいたwebデザインを担当いたしました。",
            feature01: "",
            feature02: "",
            imgSrc: require("~/assets/images/img_archive_hiroshima-oyster.jpg"),
            detailSrc: require("~/assets/images/img_detail_hiroshima-oyster.png"),
            anchor: "https://suigunnosato.com/",
          },
          {
            id: 2,
            date: "2021/09~",
            title: "活けす料理 水軍の郷",
            type: "nishimura", // nishimura, phonogram, personal
            articleType: 1,
            category: ["UX","Design"],
            subtitle: "酒処 東広島市西条の料亭の主力商品を打ち出した店舗サイトリニューアル",
            feature01: "女性を主にターゲットにした単価がやや高めの料理店で、写真を主に店舗のイメージが伝わりやすいwebサイトを心掛けました。",
            feature02: "前任のデザイナーが退職済みで、開発が中止していた制作案件を引き継ぐ形で制作いたしました。wordpressの固定ページ機能に直でコーディングしていたものが制作のボトルネックになっていたため、一度タスクランナー(Node.js)の導入から着手いたしました。",
            // results: "地元メディア(ローカルTV番組・地元紙)やカード系会社様のパンフレットに継続してメディア掲載を取り上げて頂いております。",
            imgSrc: require("~/assets/images/img_archive_suigunnosato.jpg"),
            detailSrc: require("~/assets/images/img_detail_suigunnosato.png"),
            anchor: "https://suigunnosato.com/",
          },
          {
            id: 3,
            date: "2020/12~",
            title: "炉 本通り 然然",
            type: "nishimura", // nishimura, phonogram, personal
            articleType: 1,
            category: ["UI","Design"],
            subtitle: "2020年6月開店 広島中心地の話題店",
            feature01: "女性を主にターゲットにした単価がやや高めの料理店で、写真を主軸に店舗のイメージが伝わりやすいwebサイトを心掛けました。",
            feature02: "前任のデザイナーが退職済みで、制作が中止していた案件を引き継ぐ形で制作いたしました。引継ぎ当初はwordpressの固定ページ機能に直でコーディングしていたものがボトルネックになっていたため、一度Node.jsの導入から着手いたしました。",
            results: "地元メディア(ローカルTV番組・地元紙)やカード系会社様のパンフレットに継続してメディア掲載を取り上げて頂いております。",
            imgSrc: require("~/assets/images/img_archive_irori-sasa.jpg"),
            detailSrc: require("~/assets/images/img_detail_irori-sasa.png"),
            anchor: "https://irori-sasa.jp/",
          },
          {
            id: 4,
            date: "2020/08",
            title: "医療法人 せいわ会",
            type: "phonogram",
            category: ["Wordpress", "Vuejs", "Corporate", "Recruit"],
            subtitle: "コーポレート＆採用サイトの作成",
            description: "医療法人 せいわ会さまが2020年6月に開院した、\r\n広島中央リハビリテーション病院のWebサイト&採用サイトを構築いたしました。",
            feature01: "コーポレートサイトでは、「施設の情報」、「入院までの流れ」といった利用者が知りたい情報をわかりやすくまとめております。\r\nまた、簡単に入院費用のシミュレーションができるページを作成しました。実際にサービスを利用するユーザー層や、潜在層ユーザーがサービスの利用までをイメージしやすくなるよう情報を設計しております。",
            feature02: "採用サイトでは、求職者の方がすぐに採用担当者様に応募ができるよう、Wordpressの記事で採用の募集要項を作成し、問い合わせフォームとIndeedやGoogleの仕事検索にも連携させています。",
            results: "公開1か月で10件もの採用問い合わせ達成。\r\nCV率1.7%と、上々の滑り出しとなりました。",
            imgSrc: require("~/assets/images/img_archive_hirochu-rh.jpg"),
            detailSrc: require("~/assets/images/img_detail_hirochu-rh.png"),
            anchor: "https://hirochu-rh.jp/",
          },
          {
            id: 5,
            date: "2020/04",
            title: "マツダ株式会社",
            type: "phonogram",
            category: ["Wordpress"],
            subtitle: "社内報の作成",
            description: "マツダ株式会社様の社内報の制作を担当いたしました。\r\nWordpressの独自テーマの開発にあたり、先方のシステム担当者様と弊社制作チームで協力いたしました。",
            feature01: "独自テーマを作成するにあたり、Wordpressデフォルトの機能と追加プラグインの機能変更を実施しております。",
            feature02: "弊社が開発したソースコードを納品後、クライアント様の作業ミスでWordpressが本番環境で正常に動作しない不具合に対応する場面がありました。サーバー関連の知識を要する対応のため、これまでのWordpressの制作案件で培ってきたノウハウが活かせた仕事となりました。",
            imgSrc: require("~/assets/images/img_archive_mazda.jpg"),
            detailSrc: require("~/assets/images/img_detail_mazda.png"),
            anchor: null,
          },
          {
            id: 6,
            date: "2019/09",
            title: "ひろしま美術館",
            type: "phonogram",
            category: ["Renewal"],
            subtitle: "リニューアル＆Dwテンプレート設計",
            description: "ひろしま美術館さまのサイトリニューアルに伴い、Webサイトの制作を行いました。",
            feature01: "サイトリニューアルに加え、web担当者様のご要望に合わせ、先方でも展示品の新規ページ制作が行えるよう、Dreamweaverを使用したベースコーディングを行いました。\r\nそのため、簡単にページ制作が行えるようDreamweaverのテンプレートファイルの設計も行っております。",
            imgSrc: require("~/assets/images/img_archive_hiroshima-museum.jpg"),
            detailSrc: require("~/assets/images/img_detail_hiroshima-museum.png"),
            anchor: "https://www.hiroshima-museum.jp/",
          },
          {
            id: 7,
            date: "2019/05",
            title: "近畿日本ツーリスト中国四国",
            type: "phonogram",
            category: ["Wordpress","Service","Renewal"],
            subtitle: "Wordpressテーマリニューアル",
            description: "近畿日本ツーリスト中国四国様のwebサイトリニューアルに伴い、Webサイトの制作とWordpressの更新作業を行いました。",
            feature01: "デザインの刷新に伴い、オリジナルテーマでの制作を行いました。\r\nまた、リニューアル前では脆弱性が発見されたバージョンのWordpressが既にインストールされていたため、Wordpress本体ファイルのアップデートを行い、既存ブログの整理、リニューアル前の記事データの移行作業を行っております。",
            imgSrc: require("~/assets/images/img_archive_kntcs.jpg"),
            detailSrc: require("~/assets/images/img_detail_kntcs.png"),
            anchor: "https://www.kntcs.co.jp/",
          },
          {
            id: 8,
            date: "2019/03",
            title: "近畿日本ツーリスト中国四国",
            type: "phonogram",
            category: ["Wordpress","Security"],
            subtitle: "Wordpress セキュリティ対策",
            description: "Wordpressのセキュリティ対策を実施いたしました。",
            feature01: "クライアント様のご要望により、Wordpressのセキュリティ対策を行いました。IPAから勧告されていたセキュリティ情報を基に、Wordpress4.7.xバージョンの標準セキュリティ対策を実施しております。\r\n \r\n【参考】\r\n 『WordPress の脆弱性対策について』- IPA 情報処理推進機構\r\n( https://www.ipa.go.jp/security/ciadr/vul/20170206-wordpress.html )\r\n\r\n IPAテクニカルウォッチ - 『CMSを用いたウェブサイトにおける情報セキュリティ対策のポイント』\r\n( https://www.ipa.go.jp/files/000054743.pdf ) ",
            imgSrc: require("~/assets/images/img_archive_kntcs.jpg"),
            detailSrc: require("~/assets/images/img_detail_kntcs.png"),
            anchor: "https://www.kntcs.co.jp/",
          },
          {
            id: 9,
            date: "2018/12",
            title: "Sen社会保険労務士法人",
            type: "phonogram",
            category: ["Wordpress","Service"],
            subtitle: "障害年金相談窓口 ソシオノーム - 傷病別の受給事例",
            description: "わかりにくい障害年金の受給ケースを実際の事例を基にWordpressの記事として症例別に紹介。",
            feature01: "主にWordpressでの「お知らせ」ブログと「症例別の受給事例」ブログの組み込みを担当させていただきました。<br>特に、「症例別での受給事例」ブログでは、通常の記事を表示させる一覧画面・カテゴリ別画面・詳細画面を作成するだけではなく、検索機能も追加し、ユーザーが知りたい症例にたどり着くことができる機能を実施しました。",
            results: "リニューアル前と比較し、アクセス数3倍に。",
            imgSrc: require("~/assets/images/img_archive_socio-sr.jpg"),
            detailSrc: require("~/assets/images/img_detail_socio-sr.png"),
            anchor: "https://socio-sr.com/",
          },
          {
            id: 10,
            date: "2018/11",
            title: "株式会社エムネス",
            type: "phonogram",
            category: ["Angular","SPA","Service"],
            subtitle: "遠隔画像診断 LOOKREC",
            description: "株式会社エムネス様のエンジニアと協働。<br>クラウド型医療システム「LOOKREC」を開発。<br><br>【参考】<br><a href='https://www.mnes.org/lookrec/' target='_blank' rel='noopener'>LOOKRECとは？ - 株式会社エムネス </a>",
            feature01: "株式会社エムネス様が提供する医師向け画像診断クラウドサービス、「LOOKREC」の「電子カルテ」に伴うフロントエンド開発を主に担当いたしました。\r\n当サービスを利用する医師が入力作業を繰り返すにあたり、UIに配所したインタフェースの作成に注力いたしました。\r\nコーディング面ではエムネス様側の要望により、Angular.jsを利用したフレームワークでの開発を実施。加えて、弊社の通常業務で開発する企業サイトとは異なるアプリケーション向けのCSS設計を採用し、効率的な開発を行いました。",
            results: "各メディア（Web・民法）、Google社に掲載いただいております。\r\n\r\n<a href='https://www.mnes.org/news/884' target='_blank' rel='noopener'> - 株式会社エムネス「ワールドビジネスサテライトに取り上げていただきました。」</a><br><a href='https://cloud.google.com/blog/ja/topics/customers/mens-app-engine-kubernetes-engine' target='_blank' rel='noopener'> - Google Cloud ブログ</a>",
            imgSrc: require("~/assets/images/img_archive_lookrec.jpg"),
            detailSrc: require("~/assets/images/img_detail_lookrec.png"),
            anchor: "https://phr.lookrec.com/login-ja.html",
          },
          {
            id: 11,
            date: "2018/08",
            title: "株式会社アババイ",
            type: "phonogram",
            category: ["BoltCMS","Corporate","CRM"],
            subtitle: "CRMと連携したオリジナルCMSテーマの開発",
            description: "名古屋に本社を置く建築業界のWebサイトに特化したWeb制作会社、<a href='https://ababai.co.jp/' target='_blank' rel='noopener'>アババイ</a>様の業務用CMS&CRM（通称:「アバラック2」）を制作いたしました。",
            feature01: "海外CMSの「Bolt CMS」を利用し、Webに明るくない建築会社様・工務店様でも簡単にWebサイトを更新し、「イベント」や「お知らせ」の情報をエンドユーザーに向けて発信できる機能を構築いたしました。",
            results: "アババイ様のコーポレートサイトをはじめ、全国の建築事業者のWebサイトに開発した製品が使用されております。<br><br>【参考】<br><a href='https://ababai.co.jp/case_cat/case01/' target='_blank' rel='noopener'>株式会社アババイ - 制作実績</a>",
            imgSrc: require("~/assets/images/img_archive_ababai.jpg"),
            detailSrc: require("~/assets/images/img_detail_ababai.png"),
            anchor: "https://ababai.co.jp/",
          },
          {
            id: 12,
            date: "2018/03",
            title: "株式会社サタケ",
            type: "phonogram",
            category: ["Brand"],
            subtitle: "ブランドサイトのフロントエンド",
            description: "精米機メーカーのサタケ様のブランドサイトをシングルページWebサイトとして制作いたしました。<br>サタケ様の長い歴史を1ページで振り返り、求職者の方に向けて訴求しております。",
            feature01: "主に担当したのはフロントエンドでの設計です。<br>JQueryプラグインの選定とスクリプト関連のベースコーディング・他のコーダーへの作業指示出し等を行いました。",
            imgSrc: require("~/assets/images/img_archive_satake-brand.jpg"),
            detailSrc: require("~/assets/images/img_detail_satake-brand.png"),
            anchor: "https://satake-japan.co.jp/brand/",
          },
          {
            id: 13,
            date: "2018/03",
            title: "株式会社サタケ",
            type: "phonogram",
            category: ["MovableType","Corporate","Renewal"],
            subtitle: "中規模コーポレートサイトリニューアル",
            description: "精米機メーカーのサタケ様のコーポレートサイトをリニューアルいたしました。リニューアルするにあたり、MovableTypeの組み込みと各ブログの構築を担当いたしました。",
            feature01: "リニューアル以前は約300ページ程度の静的ファイルで作成されていた「製品情報」ページ群を、MovableTypeの「製品ブログ」の記事としてまとめました。Webスクレイピングで技術検証を行い、プログラミングで記事作成数時の工数を削減できるかどうかの調査を実施。開発も担当させていただきました。",
            feature02: "加えて、「お知らせ」ブログの開発も担当させていただきました、約10年も運用を続けているWebサイトのため、記事の情報を「簡潔に・わかりやすく」まとめ、ストレスの少ない運用・閲覧ができるように開発しております。",
            imgSrc: require("~/assets/images/img_archive_satake-co.jpg"),
            detailSrc: require("~/assets/images/img_detail_satake-co.png"),
            anchor: "https://satake-japan.co.jp/",
          },
          {
            id: 14,
            date: "2018/02",
            title: "エネルギア・コミュニケーションズ",
            type: "phonogram",
            category: ["Vuejs","Service","Renewal"],
            subtitle: "サービスサイトリニューアル",
            description: "広島のTVCM等でおなじみの「MEGAEGG」、株式会社エネルギア・コミュニケーションズ様のリニューアル案件に携わりました。",
            feature01: "協力企業とともに各ページのマークアップを行っております。<br>大規模サイトでのCDGルール（CSS設計）の重要性を学ばせていただきました。",
            feature02: "また、リニューアルに伴い「料金シミュレーション」ページの作成をVue.jsで行いました。利用者側にとってわかりにくい料金プランをわかりやすく。Vus.jsでの開発とシステムの連携を行いました。",
            imgSrc: require("~/assets/images/img_archive_megaegg.jpg"),
            detailSrc: require("~/assets/images/img_detail_megaegg.png"),
            anchor: "https://www.megaegg.jp/service/fiber/plan.html",
          },
        ]
      }
    },
    methods: {
      move(id) {
        this.$router.push(`/archive/${id}`);
      }
    },
    computed: {
      matched: function() {
        return this.items.filter(el => {

          if (this.checkedCareer == '') return true; // 初期表示
          if (this.checkedCareer != '')

            if (this.checkedCategory != '') {

              const categoryArr = Object.values(el.category);
              const checkboxArr = Object.values(this.checkedCategory);

              // 積集合(=重複した値)を返す
              const uniqueArrSet = categoryArr.filter((val) => {
                return checkboxArr.indexOf(val) !== -1 && this.checkedCareer == el.type;
              });
              
              if (uniqueArrSet.length) return true;

            } else {
              return el.type === this.checkedCareer;
            }
        })
      }
    }
  }
</script>

