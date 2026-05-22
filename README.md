# hi-concept

A Claude Skill for generating a **high-concept** — a one-phrase brand idea that pulls you out of price competition and becomes the backbone of all communications (website, pitch, social, ads, design).

> **Не слоган. Не миссия. Не описание процесса.** Это смысловой позвоночник — из него выводятся Hero-копирайт, About, voice & tone и направление дизайна.

Скилл подходит для двух типов брендов:

- **Personal brand** — эксперт, спикер, коуч, консультант, ремесленник.
- **Product / Service brand** — SaaS, B2B/B2C сервис, e-com, физический продукт.

Методология — синтез четырёх школ: Анатолий Сульянов (3 опоры), Donald Miller (StoryBrand), April Dunford (Obviously Awesome), Chip & Dan Heath (Made to Stick).

## Что внутри

```
hi-concept/
├── SKILL.md                          # главный entry-point с frontmatter
├── README.md                         # этот файл
├── LICENSE                           # MIT
├── references/
│   ├── methodology.md                # что такое хай-концепт, 3 опоры, формулы
│   ├── questionnaire.md              # 6 блоков интервью + правила проведения
│   ├── validation.md                 # 11 критериев + scoring + brand-swap test
│   ├── archetypes.md                 # 12 Jungian архетипов + voice + design tokens
│   ├── examples.md                   # 40+ эталонных концептов
│   └── anti-patterns.md              # antiпримеры + anti-slop blacklist
├── prompts/
│   ├── interview-system.md           # system prompt для интервью
│   ├── divergent.md                  # генерация одного варианта (personal)
│   ├── divergent-product.md          # генерация для product/service brand
│   ├── judge.md                      # LLM-судья по 11 критериям
│   └── refine.md                     # refine выбранного варианта
└── examples/
    ├── personal-coach.md             # фитнес-коуч 40+ (personal brand)
    └── product-saas.md               # нишевый CRM (product brand)
```

## Установка

### Как Claude Skill (рекомендуется)

```bash
git clone https://github.com/<your-handle>/hi-concept.git ~/.claude/skills/hi-concept
```

После этого скилл доступен в Claude Code: автоматически активируется по триггерам («сделай хай-концепт», «нужен хай-концепт», «помоги с позиционированием», «high concept», «brand positioning»), либо запустить вручную через `/hi-concept`.

### Как референс / промпт-пак

Файлы можно использовать **без Claude Code** — просто открой `SKILL.md` и `prompts/*.md`, копируй промпты в любой LLM (Claude / ChatGPT / Gemini). Методология та же.

## Как использовать

1. **Запустить скилл** в любом проекте где нужен концепт. В Claude Code: «Сделай хай-концепт для моего бренда» или `/hi-concept`.
2. **Передать контекст** — имя, ниша, ЦА, текущая боль, существующие формулировки (если есть).
3. **Пройти интервью** — 6 коротких блоков (10-20 минут разговора).
4. **Получить 3 варианта** — divergent-стратегия, разные angles (pain / transformation / narrowing).
5. **Validation** — каждый вариант проверяется по 11 критериям, anti-slop blacklist и brand-swap test.
6. **Выбрать + refine** — пользователь выбирает один, может подкрутить.
7. **Готовый артефакт** — JSON-структура для downstream-задач (Hero, About, copy, design direction).

См. [`examples/personal-coach.md`](examples/personal-coach.md) и [`examples/product-saas.md`](examples/product-saas.md) — два прогона end-to-end.

## Ключевые принципы

### Концепт нельзя выдумать в кабинете

Самые сильные формулировки — в **речи аудитории**. «Устал от...», «бесит когда...», «хочу чтобы было просто...». Поэтому интервью — обязательный шаг. Без brief / интервью генерация даст slop.

### Divergent → convergent

Не один концепт за раз, а **3 разных angle параллельно** (Pain → Relief, Transformation, Narrowing). Высокая температура (0.85) на divergent, потом LLM-judge с rubric'ом отбирает сильное.

### Anti-slop как обязательная гигиена

«Премиальное качество», «индивидуальный подход», «лучший на рынке» и ~30 других фраз — автоматическая отбраковка. Сильный концепт может звучать «не как все», но это **не должно быть AI slop**.

### 11 критериев, минимум 9 из 11

Объясняется за 10 секунд. Помещается в одно предложение. Вызывает эмоцию. Провоцирует вопрос «как это?». Обесценивает конкурентов без прямой атаки. Заставляет конкурентов оправдываться. Меняет критерий сравнения. Естественно генерирует UGC. Работает как позвоночник. Есть конкретная боль. Есть понятный результат.

### Архетип определяет голос

12 Jungian архетипов — Hero, Rebel, Sage, Caregiver, Creator, Explorer, Magician, Ruler, Lover, Jester, Everyman, Innocent. Из архетипа выводятся voice, лексика, design direction.

## Cost / budget

При использовании Claude API на один концепт:

- Интервью: ~15-30K tokens
- Divergent (3 параллельных): ~10K
- Judge: ~6.5K
- Self-Refine (если нужен): +×2

Total — **~50-70K tokens** (≈ $0.30-0.50 на Claude Opus с prompt caching).

**Prompt caching на system-prompts обязателен** — иначе стоимость ×3-5.

## Источники

- **Анатолий Сульянов** — методология «High-Concept как основа бизнеса» (3 опоры, 5 эффектов, 11 критериев)
- **Donald Miller** — *Building a StoryBrand* (HarperCollins, 2017)
- **April Dunford** — *Obviously Awesome* (2019)
- **Alex Osterwalder** — *Value Proposition Design* (2014)
- **Chip & Dan Heath** — *Made to Stick* (Random House, 2007)
- **Al Ries, Jack Trout** — *Positioning* (1981); *22 Immutable Laws of Marketing* (1993)
- **Justin Wyatt** — *High Concept: Movies and Marketing in Hollywood* (UT Press, 1994)
- **Carol S. Pearson** — *The Hero Within* (1986)
- **arXiv 2303.17651** — *Self-Refine: Iterative Refinement with Self-Feedback*
- **arXiv 2507.02564** — *LLMREI*

Полный список — в [`references/methodology.md`](references/methodology.md).

## Развитие скилла

Скилл предполагает **доработку на конкретном проекте**:

- Расширение anti-slop blacklist своими наблюдениями («домашние» клише в вашей нише).
- Дополнительные эталоны в `references/examples.md` из вашей индустрии.
- Локальные адаптации под язык / культурный контекст.

Если у вас есть улучшения — PR welcome. Особенно ценны:

- Новые отраслевые эталоны
- Языковые версии (English, Spanish, etc.)
- Доработки промптов под новые модели

## Limitations

- **Не для нейминга.** Хай-концепт — это смысл, не название. Нейминг — отдельная дисциплина.
- **Не для слоганов.** Слоган короче и эмоциональнее, концепт — методологически глубже.
- **Не для voice gaидов в отрыве.** Сначала концепт, потом voice.
- **Не для копирайта лендинга.** Копирайт — downstream-задача после концепта.
- **Не для бренд-стратегии целиком.** Стратегия = концепт + visual identity + naming + ... — это шире.
- **Качество концепта = качество интервью.** Если пользователь даёт уклончивые ответы, концепт будет общим. Скилл — инструмент, не магия.

## License

MIT — см. [LICENSE](LICENSE).

Свободно использовать, модифицировать, распространять. Только сохраняйте credit на источники методологии (Сульянов, Miller, Dunford, Heath и т.д.) если будете цитировать.
