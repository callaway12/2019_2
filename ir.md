## Information Retriever

* 회수율 & 정확도
    - effectiveness
        - how 정확
    - efficiency
        - how 빠르게
* Evaluation
    - 답을 알려주는거
    - 찾는거
* User & Information Need

* Big Issue
    - Relevence
        - Effecitvenss Ranking
        - Ranking Alg
        - Statistical Model
    - Evaluation
        - Testing & Measuring
    - Information Needs
        - User interaction

* Search Engine
    - Performance
        - Efficient Search & Indexing
    - Incorporating new data
        - Crwaling 
            - Coverage & Freshness
    - Scalability
        - Growing with data & user
        - 분산처리
    - Adaptability
        - Tunning for application
    - Specific Problem
        - e.g spam

* Indexing Process
    - Text acquisition
        - identifies and stores documents for indexing
    - Text transformation
        - index terms or features
    - Index creation
        - creates data structures for fast searching

* Query Process
    - User interaction
        - help creation and refinement of query
    - Ranking
        - uses query and indexes for generating ranked list of docs
    - Evaluation
        - measures effectiveness and efficiency

* Crawler
    - crwal informs for search engine
        - web, enterprise, desktop
    - sulfs through *links*

* Text Acquisition
- Feeds
    - Real-time streams
        - web, news, blogs, video, radio, tv
    - RSS is common standard
        - RSS "reader" provide XML to search engine
- Conversion
    - docs -> consistent text + metadata format
        - HTML, XML, Word, PDF -> XML
    - encoding for languages
        - UTF-8
- Document data store
    - Text, metadata related content for Docs
        - Metadata -> information about docs, type and creation date
        - links, anchor text
    - Fast access
        -result list generation
    - Can use for realtional db system
    
* Text Transformation
- Parser
    - text *tokens* in the docs to recognize structural elements
        - title, links, headings
    - *Tokenizer* recognizes "words" in text
        - 대문자, 콤마 등등을 조심해야함
    - HTML XML often used to specify structure
- Stopping
    - Remove common words
        - and ,or, the, in, etc
    - can be impact on efficiency and effectiveness
- **Stemming**
    - computer, compute, computing, computers
    - Effective, but not all queries
    - 언어마다 차이가 있음
- Link Analysis
    - use of *links* and *anchor text*
    - identifies *popularity* and *community* information
        - Page Rank
    - Anchor text 중요
    - web search 에 중요
- Information Extraction
    - class 로 정보 구분, loactions, companies
- Classifier
    - class-related meatadata for docs
        - labels to docs
        - topics, reading levels, sentiment, genre
    - Use depends on app
* Index Creation
    - Doc Statics
        - Gathers counts and pos of words and features
        - used in ranking alg
    - Weighting
        - index terms weighting
        - ranking alg
        - **tf.idf weight**
            - combination of *term frequency* in docs and *inverse* doc frequency in collection
    - Inversion
        - Core of indexing process
        - doc-term inforamtion -> term-doc for indexing
        - Format for fast query processing
    - Index Distribution
        - across multiple computers and sites
        - Essential for fast query
        - variations
            - Doc distribution, term distribution, replication
        - P2P and Distributed IR involve search across multiple sites
* User Interaction
- Query transformation
    - inlcudes text transformation tech
    - *Spell checking* *Query suggestion*
    - *Query expansion* and *relevance feedback* modify original query with additional terms
- Results output
    - ranked doc for query
    - snippets to show how queries match doc
    - highlights words and passage
    - retrieves appropriate advertising in many applications
    - clustering and visualization
* Ranking
- Scoring
    - \sum q_i d_i
    - $\sum_ q_i d_i$
        - q_i -> query, di -> doc term wieths for term i
- Optimization
    - term-at-a-time vs doc-at-a-time  processing
    - safe vs unsafe   optimization
- Distribution
    - distributed env
    - *Quert broker* distributes queries and assembles results
    - *Caching* form of distributed searching
* Evaluation
- Logging
    - user queries & interaction  for effectiveness and effeciency
- Ranking analysis
    - Measuring and tuning *ranking* **effectiveness**
- Performance analysis
    - Measuring and tuning *system* **efficiency**
