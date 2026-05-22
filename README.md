# hi-concept

[🇷🇺 Русский](#русская-версия) · [🇬🇧 English](#english-version)

A [Claude Skill](https://docs.claude.com/en/docs/claude-code/skills) for generating a **brand high-concept** — a one-phrase idea that pulls a brand out of price competition and serves as the backbone of all communications.

---

## Русская версия

Claude Skill для генерации **хай-концепта** — одной фразы, которая выводит бренд из ценовой конкуренции и становится позвоночником всех коммуникаций (сайт, питч, соцсети, реклама, дизайн).

> **Не слоган. Не миссия. Не описание процесса.** Это смысловой позвоночник — из него выводятся Hero-копирайт, About, voice & tone и направление дизайна.

Подходит для двух типов брендов:

- **Personal brand** — эксперт, спикер, коуч, консультант, ремесленник, автор.
- **Product / Service brand** — SaaS, B2B/B2C сервис, e-com, физический продукт.

Методология — синтез четырёх школ: Анатолий Сульянов (3 опоры), Donald Miller (StoryBrand), April Dunford (Obviously Awesome), Chip & Dan Heath (Made to Stick).

### Что внутри

```
hi-concept/
├── SKILL.md                          # главный entry-point с frontmatter
├── README.md                         # этот файл
├── LICENSE                           # MIT
├── references/
│   ├── methodology.md                # 3 опоры, формулы (Сульянов / StoryBrand / Hollywood / VPC)
│   ├── questionnaire.md              # 6 блоков интервью + правила
│   ├── validation.md                 # 11 критериев + brand-swap test + ownability
│   ├── archetypes.md                 # 12 Jungian архетипов + voice + design tokens
│   ├── examples.md                   # 40+ эталонных концептов
│   └── anti-patterns.md              # blacklist + 5 ловушек LLM
├── prompts/
│   ├── interview-system.md           # system для интервью
│   ├── divergent.md                  # генерация (personal brand)
│   ├── divergent-product.md          # генерация (product / service)
│   ├── judge.md                      # LLM-судья по 11 критериям
│   └── refine.md                     # refine выбранного варианта
└── examples/
    ├── personal-coach.md             # фитнес-коуч 40+ (personal brand)
    └── product-saas.md               # нишевый CRM (product brand)
```

### Установка

**Как Claude Skill (рекомендуется):**

```bash
git clone https://github.com/mower07/high-concept-skill.git ~/.claude/skills/hi-concept
```

Скилл подхватывается Claude Code автоматически. Триггеры: «нужен хай-концепт», «помоги с позиционированием», «high concept», «brand positioning», `/hi-concept`.

**Как промпт-пак** (без Claude Code) — открой `SKILL.md` и `prompts/*.md`, копируй промпты в любой LLM (Claude / ChatGPT / Gemini). Методология та же.

### Как использовать

1. **Запустить скилл** — «Сделай хай-концепт для моего бренда» или `/hi-concept`.
2. **Передать контекст** — имя, ниша, ЦА, текущая боль, существующие формулировки.
3. **Пройти интервью** — 6 коротких блоков (10-20 минут разговора).
4. **Получить 3 варианта** — divergent-стратегия, разные angles (pain / transformation / narrowing).
5. **Validation** — каждый вариант проверяется по 11 критериям, anti-slop blacklist и brand-swap test.
6. **Выбрать + refine** — пользователь выбирает один, может подкрутить.
7. **Готовый артефакт** — JSON-структура для downstream-задач (Hero, About, copy, design direction).

См. [`examples/personal-coach.md`](examples/personal-coach.md) и [`examples/product-saas.md`](examples/product-saas.md) — два прогона end-to-end.

### Ключевые принципы

**Концепт нельзя выдумать в кабинете.** Самые сильные формулировки — в речи аудитории. «Устал от...», «бесит когда...», «хочу чтобы было просто...». Без интервью генерация даст slop.

**Divergent → convergent.** Не один концепт за раз, а **3 разных angle параллельно** (Pain → Relief, Transformation, Narrowing). Высокая температура (0.85) на divergent, потом LLM-judge с rubric'ом отбирает сильное.

**Anti-slop как обязательная гигиена.** «Премиальное качество», «индивидуальный подход», «лучший на рынке» и ~30 других фраз — автоматическая отбраковка. Сильный концепт может звучать «не как все», но это **не должно быть AI slop**.

**11 критериев, минимум 9 из 11.** Объясняется за 10 секунд. Одно предложение. Вызывает эмоцию. Провоцирует «как это?». Обесценивает конкурентов. Заставляет оправдываться. Меняет критерий сравнения. Генерирует UGC. Работает как позвоночник. Есть конкретная боль. Есть понятный результат.

**Архетип определяет голос.** 12 Jungian архетипов — Hero, Rebel, Sage, Caregiver, Creator, Explorer, Magician, Ruler, Lover, Jester, Everyman, Innocent.

### Cost / budget

При использовании Claude API на один концепт:

- Интервью: ~15-30K tokens
- Divergent (3 параллельных): ~10K
- Judge: ~6.5K
- Self-Refine (если нужен): +×2

Total — **~50-70K tokens** (≈ $0.30-0.50 на Claude Opus с prompt caching).

**Prompt caching на system-prompts обязателен** — иначе стоимость ×3-5.

### Источники

- **Анатолий Сульянов** — методология «High-Concept как основа бизнеса»
- **Donald Miller** — *Building a StoryBrand* (HarperCollins, 2017)
- **April Dunford** — *Obviously Awesome* (2019)
- **Alex Osterwalder** — *Value Proposition Design* (2014)
- **Chip & Dan Heath** — *Made to Stick* (Random House, 2007)
- **Al Ries, Jack Trout** — *Positioning* (1981); *22 Immutable Laws of Marketing* (1993)
- **Justin Wyatt** — *High Concept: Movies and Marketing in Hollywood* (UT Press, 1994)
- **Carol S. Pearson** — *The Hero Within* (1986)
- **arXiv 2303.17651** — *Self-Refine: Iterative Refinement with Self-Feedback*

Полный список — в [`references/methodology.md`](references/methodology.md).

### Развитие скилла

Скилл предполагает доработку на конкретном проекте:

- Расширение anti-slop blacklist своими наблюдениями.
- Дополнительные эталоны в `references/examples.md` из вашей индустрии.
- Локальные адаптации под язык / культурный контекст.

PR welcome. Особенно ценны: новые отраслевые эталоны, языковые версии, доработки промптов под новые модели.

### Ограничения

- **Не для нейминга.** Хай-концепт — смысл, не название.
- **Не для слоганов.** Слоган короче и эмоциональнее, концепт — методологически глубже.
- **Не для voice-гайдов в отрыве.** Сначала концепт, потом voice.
- **Не для копирайта лендинга.** Копирайт — downstream-задача после концепта.
- **Не для бренд-стратегии целиком.** Это шире (concept + visual identity + naming + …).
- **Качество концепта = качество интервью.** Если ответы уклончивые — концепт будет общим. Скилл — инструмент, не магия.

### Лицензия

MIT — см. [LICENSE](LICENSE). Свободно использовать, модифицировать, распространять. Только сохраняйте credit на источники методологии (Сульянов, Miller, Dunford, Heath и т.д.) если будете цитировать.

---

## English version

A [Claude Skill](https://docs.claude.com/en/docs/claude-code/skills) for generating a **high-concept** — a one-phrase brand idea that pulls a brand out of price competition and serves as the backbone of all communications (website, pitch, social, ads, design).

> **Not a tagline. Not a mission statement. Not a process description.** A high-concept is the semantic spine — Hero copy, About, voice & tone, and design direction all flow from it.

Works for two brand types:

- **Personal brand** — expert, speaker, coach, consultant, craftsman, author.
- **Product / Service brand** — SaaS, B2B/B2C service, e-commerce, physical product.

Methodology — a synthesis of four schools: Anatoly Sulyanov (3 pillars), Donald Miller (StoryBrand), April Dunford (Obviously Awesome), Chip & Dan Heath (Made to Stick).

### What's inside

```
hi-concept/
├── SKILL.md                          # main entry-point with frontmatter
├── README.md                         # this file
├── LICENSE                           # MIT
├── references/
│   ├── methodology.md                # 3 pillars, formulas (Sulyanov / StoryBrand / Hollywood / VPC)
│   ├── questionnaire.md              # 6 interview blocks + rules
│   ├── validation.md                 # 11-criteria rubric + brand-swap + ownability
│   ├── archetypes.md                 # 12 Jungian archetypes + voice + design tokens
│   ├── examples.md                   # 40+ benchmark concepts
│   └── anti-patterns.md              # blacklist + 5 LLM traps
├── prompts/
│   ├── interview-system.md           # interview system prompt
│   ├── divergent.md                  # generation (personal brand)
│   ├── divergent-product.md          # generation (product / service)
│   ├── judge.md                      # LLM judge against 11 criteria
│   └── refine.md                     # refine a chosen variant
└── examples/
    ├── personal-coach.md             # fitness coach for 40+ (personal brand)
    └── product-saas.md               # niche CRM (product brand)
```

> **Note on language.** The skill is written in Russian (interview prompts, examples, anti-slop blacklist focused on Russian-language clichés). The methodology itself is universal and Claude will happily run the process in English — but you'll want to translate the anti-slop list to catch English clichés ("world-class", "best-in-class", "cutting-edge" — see `references/anti-patterns.md` for a starter EN list). PRs with a full English port are very welcome.

### Installation

**As a Claude Skill (recommended):**

```bash
git clone https://github.com/mower07/high-concept-skill.git ~/.claude/skills/hi-concept
```

Claude Code picks it up automatically. Triggers: "need a high-concept", "help with positioning", "brand positioning", "high concept", `/hi-concept`.

**As a prompt pack** (without Claude Code) — open `SKILL.md` and `prompts/*.md`, paste prompts into any LLM (Claude / ChatGPT / Gemini). The methodology is the same.

### How to use

1. **Start the skill** — "Generate a high-concept for my brand" or `/hi-concept`.
2. **Provide context** — name, niche, target audience, current pain, existing formulations.
3. **Go through the interview** — 6 short blocks (10-20 minutes of conversation).
4. **Get 3 variants** — divergent strategy, different angles (pain / transformation / narrowing).
5. **Validation** — each variant is checked against 11 criteria, anti-slop blacklist, and brand-swap test.
6. **Pick + refine** — choose one, tweak with a free-form hint.
7. **Final artifact** — JSON structure ready for downstream tasks (Hero, About, copy, design direction).

See [`examples/personal-coach.md`](examples/personal-coach.md) and [`examples/product-saas.md`](examples/product-saas.md) for end-to-end walkthroughs.

### Key principles

**You can't invent a high-concept at a desk.** The strongest formulations live in the audience's own words. "I'm tired of...", "what drives me crazy is...", "I just want it to be simple...". Skip the interview → you get slop.

**Divergent → convergent.** Not one concept at a time, but **3 different angles in parallel** (Pain → Relief, Transformation, Narrowing). High temperature (0.85) on divergent, then an LLM judge with a rubric picks the strong ones.

**Anti-slop is mandatory hygiene.** "Premium quality", "individual approach", "industry-leading" and ~30 other phrases trigger automatic rejection. A strong concept may sound "not like everyone else" — but it must **not be AI slop**.

**11 criteria, at least 9 of 11.** Explainable in 10 seconds. One sentence. Evokes emotion. Provokes "how exactly?". Devalues competitors. Forces them to make excuses. Changes the comparison axis. Generates UGC. Works as a backbone. Names a concrete pain. Names a clear result.

**Archetype defines voice.** 12 Jungian archetypes — Hero, Rebel, Sage, Caregiver, Creator, Explorer, Magician, Ruler, Lover, Jester, Everyman, Innocent.

### Cost / budget

Per concept on the Claude API:

- Interview: ~15-30K tokens
- Divergent (3 parallel calls): ~10K
- Judge: ~6.5K
- Self-Refine (if needed): +×2

Total — **~50-70K tokens** (~$0.30-0.50 on Claude Opus with prompt caching enabled).

**Prompt caching on system prompts is mandatory** — otherwise costs go up ×3-5.

### Sources

- **Anatoly Sulyanov** — "High-Concept as the Foundation of Business" methodology (Russian-language brand school)
- **Donald Miller** — *Building a StoryBrand* (HarperCollins, 2017)
- **April Dunford** — *Obviously Awesome* (2019)
- **Alex Osterwalder** — *Value Proposition Design* (2014)
- **Chip & Dan Heath** — *Made to Stick* (Random House, 2007)
- **Al Ries, Jack Trout** — *Positioning* (1981); *22 Immutable Laws of Marketing* (1993)
- **Justin Wyatt** — *High Concept: Movies and Marketing in Hollywood* (UT Press, 1994)
- **Carol S. Pearson** — *The Hero Within* (1986)
- **arXiv 2303.17651** — *Self-Refine: Iterative Refinement with Self-Feedback*

Full list in [`references/methodology.md`](references/methodology.md).

### Extending the skill

The skill is designed to be extended per project:

- Add your own industry clichés to the anti-slop blacklist.
- Add benchmark concepts from your industry to `references/examples.md`.
- Localize for your language / cultural context.

PRs welcome. Especially valuable: new industry benchmarks, language ports (a full EN port is high-priority), prompt tuning for new models.

### Limitations

- **Not for naming.** High-concept is meaning, not a name. Naming is a separate discipline.
- **Not for taglines.** Taglines are shorter and more emotional; high-concept is methodologically deeper.
- **Not for voice guides in isolation.** Concept first, then voice.
- **Not for landing page copy.** Copy is a downstream task after the concept.
- **Not a full brand strategy.** Strategy is broader (concept + visual identity + naming + …).
- **Concept quality = interview quality.** Evasive answers → generic concept. The skill is a tool, not magic.

### License

MIT — see [LICENSE](LICENSE). Free to use, modify, and distribute. Please keep credit on the methodology sources (Sulyanov, Miller, Dunford, Heath, etc.) when citing.
