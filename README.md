# 企業情報検索ジェネレーター

法人営業担当向けに、ターゲット企業の基本情報・役員構成・サービス概要を自動で検索・要約するフローです。  
[Dify](https://dify.ai) のワークフロー機能を利用して構築されています。

## 機能
- Google検索から企業名を調査
- GPT-4o-mini による情報抽出・要約
- 役員リストやサービス概要を整理して返答

## 技術スタック
- Dify Workflow
- Google Search プラグイン
- OpenAI GPT-4o-mini

## デモ
実際に動かす → [公開チャット](https://udify.app/chat/n2U2aqlqcKusEwGK)
[企業情報検索ジェネレーター.yml](https://github.com/user-attachments/files/22588859/default.yml)

## 使い方
1. Dify アカウントを作成
2. このフローをインポート
3. APIキーを設定
4. チャットで企業名を入力すると情報が返ってきます



[Uploaapp:
  description: 企業名を入力すると自動的に検索、事業内容と今後の展望を記載します。
  icon: 🤖
  icon_background: '#FFEAD5'
  mode: advanced-chat
  name: 企業情報検索ジェネレーター
  use_icon_as_answer_icon: false
dependencies:
- current_identifier: null
  type: marketplace
  value:
    marketplace_plugin_unique_identifier: langgenius/google:0.0.9@d360bbc433f39be1b11909cb9c32e6be4a17ea06af083f9e1c7613bb802bf517
    version: null
- current_identifier: null
  type: marketplace
  value:
    marketplace_plugin_unique_identifier: langgenius/openai:0.2.6@e2665624a156f52160927bceac9e169bd7e5ae6b936ae82575e14c90af390e6e
    version: null
kind: app
version: 0.4.0
workflow:
  conversation_variables: []
  environment_variables: []
  features:
    file_upload:
      allowed_file_extensions:
      - .JPG
      - .JPEG
      - .PNG
      - .GIF
      - .WEBP
      - .SVG
      allowed_file_types:
      - image
      allowed_file_upload_methods:
      - local_file
      - remote_url
      enabled: false
      fileUploadConfig:
        audio_file_size_limit: 50
        batch_count_limit: 5
        file_size_limit: 15
        image_file_size_limit: 10
        video_file_size_limit: 100
        workflow_file_upload_limit: 10
      image:
        enabled: false
        number_limits: 3
        transfer_methods:
        - local_file
        - remote_url
      number_limits: 3
    opening_statement: ''
    retriever_resource:
      enabled: true
    sensitive_word_avoidance:
      enabled: false
    speech_to_text:
      enabled: false
    suggested_questions: []
    suggested_questions_after_answer:
      enabled: false
    text_to_speech:
      enabled: false
      language: ''
      voice: ''
  graph:
    edges:
    - data:
        isInIteration: false
        isInLoop: false
        sourceType: start
        targetType: tool
      id: 1756215314286-source-1756215379036-target
      source: '1756215314286'
      sourceHandle: source
      target: '1756215379036'
      targetHandle: target
      type: custom
      zIndex: 0
    - data:
        isInIteration: false
        isInLoop: false
        sourceType: tool
        targetType: llm
      id: 1756215379036-source-llm-target
      source: '1756215379036'
      sourceHandle: source
      target: llm
      targetHandle: target
      type: custom
      zIndex: 0
    - data:
        isInLoop: false
        sourceType: tool
        targetType: llm
      id: 1756215379036-source-17562160261840-target
      source: '1756215379036'
      sourceHandle: source
      target: '17562160261840'
      targetHandle: target
      type: custom
      zIndex: 0
    - data:
        isInIteration: false
        isInLoop: false
        sourceType: llm
        targetType: llm
      id: llm-source-1756216142596-target
      source: llm
      sourceHandle: source
      target: '1756216142596'
      targetHandle: target
      type: custom
      zIndex: 0
    - data:
        isInLoop: false
        sourceType: llm
        targetType: llm
      id: 17562160261840-source-1756216142596-target
      source: '17562160261840'
      sourceHandle: source
      target: '1756216142596'
      targetHandle: target
      type: custom
      zIndex: 0
    - data:
        isInIteration: false
        isInLoop: false
        sourceType: llm
        targetType: answer
      id: 1756216142596-source-1756216335296-target
      source: '1756216142596'
      sourceHandle: source
      target: '1756216335296'
      targetHandle: target
      type: custom
      zIndex: 0
    nodes:
    - data:
        desc: ''
        selected: false
        title: 開始
        type: start
        variables: []
      height: 52
      id: '1756215314286'
      position:
        x: 80
        y: 282
      positionAbsolute:
        x: 80
        y: 282
      selected: false
      sourcePosition: right
      targetPosition: left
      type: custom
      width: 242
    - data:
        context:
          enabled: true
          variable_selector:
          - '1756215379036'
          - text
        desc: ''
        memory:
          query_prompt_template: '{{#sys.query#}}


            {{#sys.files#}}'
          role_prefix:
            assistant: ''
            user: ''
          window:
            enabled: false
            size: 10
        model:
          completion_params:
            temperature: 0.7
          mode: chat
          name: gpt-4o-mini
          provider: langgenius/openai/openai
        prompt_template:
        - id: 35ae0431-ad01-400b-9f3a-fa920e0e4dbe
          role: system
          text: '{{#1756215379036.text#}}検索結果を元に下記を教えてください。


            ⚫︎基本情報

            会社名

            設立年月日

            所在地

            主な事業内容

            資本金'
        selected: false
        title: 基本情報
        type: llm
        variables: []
        vision:
          enabled: false
      height: 88
      id: llm
      position:
        x: 680
        y: 282
      positionAbsolute:
        x: 680
        y: 282
      selected: false
      sourcePosition: right
      targetPosition: left
      type: custom
      width: 242
    - data:
        desc: ''
        is_team_authorization: true
        output_schema: null
        paramSchemas:
        - auto_generate: null
          default: null
          form: llm
          human_description:
            en_US: used for searching
            ja_JP: used for searching
            pt_BR: used for searching
            zh_Hans: 用于搜索网页内容
          label:
            en_US: Query string
            ja_JP: Query string
            pt_BR: Query string
            zh_Hans: 查询语句
          llm_description: key words for searching
          max: null
          min: null
          name: query
          options: []
          placeholder: null
          precision: null
          required: true
          scope: null
          template: null
          type: string
        - auto_generate: null
          default: null
          form: llm
          human_description:
            en_US: Parameter defines the language to use for the Google search. It's
              a two-letter language code. (e.g., en for English, es for Spanish, or
              fr for French). Head to https://serpapi.com/google-languages for a full
              list of supported Google languages.
            ja_JP: Parameter defines the language to use for the Google search. It's
              a two-letter language code. (e.g., en for English, es for Spanish, or
              fr for French). Head to https://serpapi.com/google-languages for a full
              list of supported Google languages.
            pt_BR: Parameter defines the language to use for the Google search. It's
              a two-letter language code. (e.g., en for English, es for Spanish, or
              fr for French). Head to https://serpapi.com/google-languages for a full
              list of supported Google languages.
            zh_Hans: 此参数定义用于 Google 搜索的语言。它是一个两字母的语言代码。 (例如，en 代表英语，es 代表西班牙语，fr 代表法语)。请前往
              https://serpapi.com/google-languages 查看完整的支持 Google 语言列表。
          label:
            en_US: Language
            ja_JP: Language
            pt_BR: Language
            zh_Hans: 语言
          llm_description: Language
          max: null
          min: null
          name: hl
          options: []
          placeholder: null
          precision: null
          required: false
          scope: null
          template: null
          type: string
        - auto_generate: null
          default: null
          form: llm
          human_description:
            en_US: Parameter defines the country to use for the Google search. It's
              a two-letter country code. (e.g., us for the United States, uk for United
              Kingdom, or fr for France). Head to the https://serpapi.com/google-countries
              for a full list of supported Google countries.
            ja_JP: Parameter defines the country to use for the Google search. It's
              a two-letter country code. (e.g., us for the United States, uk for United
              Kingdom, or fr for France). Head to the https://serpapi.com/google-countries
              for a full list of supported Google countries.
            pt_BR: Parameter defines the country to use for the Google search. It's
              a two-letter country code. (e.g., us for the United States, uk for United
              Kingdom, or fr for France). Head to the https://serpapi.com/google-countries
              for a full list of supported Google countries.
            zh_Hans: 此参数定义用于 Google 搜索的国家。它是一个两字母的国家代码。 (例如，us 代表美国，uk 代表英国，fr 代表法国)。请前往
              https://serpapi.com/google-countries 查看完整的支持 Google 国家列表。
          label:
            en_US: Country
            ja_JP: Country
            pt_BR: Country
            zh_Hans: 国家
          llm_description: Country
          max: null
          min: null
          name: gl
          options: []
          placeholder: null
          precision: null
          required: false
          scope: null
          template: null
          type: string
        - auto_generate: null
          default: null
          form: llm
          human_description:
            en_US: Parameter defines from where you want the search to originate.
              If several locations match the location requested, we'll pick the most
              popular one. Head to the /locations.json API if you need more precise
              control. The location and uule parameters can't be used together. It
              is recommended to specify location at the city level in order to simulate
              a real user’s search. If location is omitted, the search may take on
              the location of the proxy.
            ja_JP: Parameter defines from where you want the search to originate.
              If several locations match the location requested, we'll pick the most
              popular one. Head to the /locations.json API if you need more precise
              control. The location and uule parameters can't be used together. It
              is recommended to specify location at the city level in order to simulate
              a real user’s search. If location is omitted, the search may take on
              the location of the proxy.
            pt_BR: Parameter defines from where you want the search to originate.
              If several locations match the location requested, we'll pick the most
              popular one. Head to the /locations.json API if you need more precise
              control. The location and uule parameters can't be used together. It
              is recommended to specify location at the city level in order to simulate
              a real user’s search. If location is omitted, the search may take on
              the location of the proxy.
            zh_Hans: 此参数定义搜索的位置。如果有多个位置与请求的位置匹配，我们将选择最受欢迎的一个。如果需要更精确的控制，请前往 /locations.json
              API。location 和 uule 参数不能同时使用。建议在城市级别指定位置，以模拟真实用户的搜索。如果省略位置，则搜索可能会采用代理的位置。
          label:
            en_US: Location
            ja_JP: Location
            pt_BR: Location
            zh_Hans: 位置
          llm_description: Location
          max: null
          min: null
          name: location
          options: []
          placeholder: null
          precision: null
          required: false
          scope: null
          template: null
          type: string
        params:
          gl: ''
          hl: ''
          location: ''
          query: ''
        provider_id: langgenius/google/google
        provider_name: langgenius/google/google
        provider_type: builtin
        selected: false
        title: GoogleSearch
        tool_configurations: {}
        tool_description: A tool for performing a Google SERP search and extracting
          snippets and webpages.Input should be a search query.
        tool_label: GoogleSearch
        tool_name: google_search
        tool_node_version: '2'
        tool_parameters:
          gl:
            type: mixed
            value: null
          hl:
            type: mixed
            value: null
          location:
            type: mixed
            value: null
          query:
            type: mixed
            value: '{{#sys.query#}}'
        type: tool
      height: 52
      id: '1756215379036'
      position:
        x: 380
        y: 282
      positionAbsolute:
        x: 380
        y: 282
      selected: true
      sourcePosition: right
      targetPosition: left
      type: custom
      width: 242
    - data:
        context:
          enabled: true
          variable_selector:
          - '1756215379036'
          - text
        desc: ''
        memory:
          query_prompt_template: '{{#sys.query#}}


            {{#sys.files#}}'
          role_prefix:
            assistant: ''
            user: ''
          window:
            enabled: false
            size: 10
        model:
          completion_params:
            temperature: 0.7
          mode: chat
          name: gpt-4o-mini
          provider: langgenius/openai/openai
        prompt_template:
        - id: 010fc1f8-34ed-4079-bac0-14472ea69dfe
          role: system
          text: '{{#1756215379036.text#}}検索結果を元に下記を教えてください。


            ・サービス概要

            主力商品やサービスの説明'
        selected: false
        title: サービス概要 (1)
        type: llm
        variables: []
        vision:
          enabled: false
      height: 88
      id: '17562160261840'
      position:
        x: 680
        y: 422.63383691611756
      positionAbsolute:
        x: 680
        y: 422.63383691611756
      selected: false
      sourcePosition: right
      targetPosition: left
      type: custom
      width: 242
    - data:
        context:
          enabled: false
          variable_selector: []
        desc: ''
        model:
          completion_params:
            temperature: 0.7
          mode: chat
          name: gpt-4o-mini
          provider: langgenius/openai/openai
        prompt_template:
        - id: e1af344f-31a2-4e2a-93f7-b62273a10c52
          role: system
          text: '{{#llm.text#}}/{{#17562160261840.text#}}

            これらの情報から企業の将来戦略として想定されるアクションの仮説を推測してください。'
        selected: false
        title: 将来戦略の仮説
        type: llm
        variables: []
        vision:
          enabled: false
      height: 88
      id: '1756216142596'
      position:
        x: 1003.1741275246488
        y: 282
      positionAbsolute:
        x: 1003.1741275246488
        y: 282
      selected: false
      sourcePosition: right
      targetPosition: left
      type: custom
      width: 242
    - data:
        answer: '1.基本情報

          {{#llm.text#}}

          2.サービス概要

          {{#17562160261840.text#}}

          3.将来戦略

          {{#1756216142596.text#}}'
        desc: ''
        selected: false
        title: 回答
        type: answer
        variables: []
      height: 141
      id: '1756216335296'
      position:
        x: 1307.1741275246488
        y: 282
      positionAbsolute:
        x: 1307.1741275246488
        y: 282
      selected: false
      sourcePosition: right
      targetPosition: left
      type: custom
      width: 242
    viewport:
      x: 82.91201163911512
      y: 131.1640938432704
      zoom: 0.5746209002728736
  rag_pipeline_variables: []
ding 企業情報検索ジェネレーター.yml…]()

