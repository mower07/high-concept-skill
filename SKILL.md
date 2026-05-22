---
name: hi-concept
description: Сгенерировать хай-концепт — смысловое ядро бренда в одной фразе, которое выводит из ценовой конкуренции и становится позвоночником всех коммуникаций. Подходит для personal brand (эксперт, спикер, консультант, коуч) и для product/service brand (SaaS, B2B/B2C услуги, e-com). Методология — синтез Анатолия Сульянова (3 опоры), Donald Miller (StoryBrand), April Dunford (Obviously Awesome), Chip & Dan Heath (Made to Stick). Триггеры — «нужен хай-концепт», «позиционирование», «big idea», «как сформулировать что мы делаем», «помоги с концептом бренда», «high concept», «brand positioning». НЕ использовать для — генерации слоганов и тэглайнов (это другое), брендового нейминга, разработки tone of voice без концепта, копирайта лендинга (это downstream-задача после концепта).
---

# Hi-Concept Skill

Хай-концепт — это **одна фраза**, которая мгновенно отвечает на вопрос «Что это и почему мне нужно?», выводит бренд из ценовой войны и становится фундаментом всех коммуникаций (сайт, питч, соцсети, реклама, дизайн).

Не слоган. Не миссия. Не описание процесса. Не список достоинств. Это **смысловой позвоночник** — из него потом выводятся Hero-копирайт, секция About, messaging, voice & tone, design direction.

## Когда использовать

- Клиенту/пользователю нужно **сформулировать позиционирование** до того как делать сайт/презентацию/питч.
- Текущая формулировка скучная, generic, попадает в anti-slop blacklist («премиальное качество», «индивидуальный подход» и т.д.) — её надо переделать.
- Нужно **выйти из ценовой конкуренции** — переключить критерий сравнения с «дешевле/быстрее» на новую ось.
- Есть бриф + ответы на вопросы про ЦА, боль, отличия — но нет финальной фразы.

## Когда НЕ использовать

- Нужен **слоган** для конкретной кампании — это другая задача (краткий emotional hook, не методологическая основа).
- Нужен **нейминг** бренда — отдельная дисциплина.
- Нужно **разработать voice & tone gaйд** в отрыве от концепта — сначала концепт, потом voice.
- Нужно написать **копирайт лендинга** — это downstream-задача, концепт должен быть готов до неё.
- Нужно сделать **бренд-стратегию целиком** (visual identity + naming + позиционирование + …) — это шире, чем хай-концепт.

## Процесс — 7 шагов

```
1. Принять контекст (brief)
2. Определить тип: personal brand или product/service brand
3. Провести интервью (6 блоков)
4. Сгенерировать 3 варианта divergent-методом (3 разных angle)
5. Прогнать через 11-критерный validation-rubric (LLM-judge)
6. Показать пользователю → выбор / отказ → finalize или refine/regenerate
7. Зафиксировать финальный артефакт
```

### Шаг 1 — Принять контекст

Спроси у пользователя или прими как вход:

- **Имя** (для personal) или **название продукта/компании** (для product).
- **Ниша / категория** (что делают).
- **ЦА** (для кого).
- **Боль клиента** (что у ЦА болит) — если уже известна.
- **Что отличает** от конкурентов — гипотеза пользователя (можно «не знаю»).
- **Существующие формулировки** — если есть текущий сайт/посты/презентация, разбери их (часто там сразу видны anti-slop фразы).

Если контекста мало — переходи к интервью, оно его соберёт.

### Шаг 2 — Определить тип

**Personal brand** — эксперт, спикер, коуч, консультант, ремесленник, автор. Фокус — «я делаю X для Y, потому что Z». Архетип чаще `Sage`, `Caregiver`, `Magician`, `Hero`.

**Product/Service brand** — SaaS, агентство, B2B/B2C сервис, e-com, физический продукт. Фокус — «продукт делает X для сегмента Y, в отличие от Z». Архетип определяется через анти-категорию. Brand-swap test обязателен (см. [`references/validation.md`](references/validation.md)).

Если непонятно — спроси «это про вас лично как эксперта или про продукт/компанию?». Не пытайся угадать — методология чуть разная.

### Шаг 3 — Провести интервью

См. [`references/questionnaire.md`](references/questionnaire.md) — 6 блоков:

1. **Боль клиента** — речь аудитории, что бесит, чего боятся
2. **Результат / трансформация** — как меняется жизнь / работа после
3. **Уникальный угол / сужение** — с кем работают, от чего отказываются, что делают иначе
4. **Враг / tension** — с каким стереотипом или ложью рынка спорят
5. **Ценности / архетип** — что для них главное, чем не хотят быть
6. **Контекст** — цифры, факты, биография

**Правила интервью:**

- Один вопрос за ход, не дамп.
- Least-to-most prompting — сначала общее, потом конкретика.
- Running summary после каждого блока — «правильно ли я понял?».
- Skip logic — если ответ чёткий, не уточняй; если уклончивый — копай с примерами.
- Прокручивай блоки **в любом порядке**, если в ходе разговора всплывает информация из другого блока — фиксируй её, не возвращай к скрипту.

System-prompt для интервью — [`prompts/interview-system.md`](prompts/interview-system.md).

### Шаг 4 — Сгенерировать 3 варианта divergent

**Стратегия — divergent-convergent.** Три параллельных LLM-вызова с **разными angles**, температура ~0.85. Получаем 3 существенно разных концепта, не 3 перефразирования одного.

**Три angle (опоры Сульянова):**

1. **Pain → Relief** — концепт формулирует избавление от конкретной боли, словами самой аудитории. См. [`prompts/divergent.md`](prompts/divergent.md) с параметром `angle=pain_relief`.
2. **Transformation** — концепт рисует переход «до → после». `angle=transformation`.
3. **Narrowing / Enemy** — концепт делает чёткий выбор и/или противопоставление лжи рынка. `angle=narrowing`.

Для product-brand — используй [`prompts/divergent-product.md`](prompts/divergent-product.md), там добавлен brand-swap test и фокус на сегмент/категорию.

**Каждый вариант — структурированный артефакт:**

```json
{
  "angle": "pain_relief | transformation | narrowing",
  "big_idea": "string (≤100 chars, одна фраза)",
  "full_description": "string (2-3 sentences, для About-секции)",
  "pillars": ["string × 3 (messaging pillars)"],
  "enemy": "string | null (с чем боремся)",
  "voice": "manifesto | expert | professional | friendly | provocative",
  "archetype": "Hero | Rebel | Sage | Caregiver | Creator | Explorer | Magician | Ruler | Lover | Jester | Everyman | Innocent",
  "test_phrase": "string (≤50 chars, как клиент расскажет другу)"
}
```

### Шаг 5 — Validation (LLM-judge)

Прогнать каждый из 3 вариантов через **11-критерный rubric** (см. [`references/validation.md`](references/validation.md)).

Правило: **сильный концепт = ≥9/11 + 0 slop-words**. Если <7/11 или есть slop-words — вариант отбрасывается, нужен regenerate.

Промпт судьи — [`prompts/judge.md`](prompts/judge.md). Можно вызывать как отдельный LLM-вызов с tool `score_concepts` или сделать inline-оценку в основном чате.

**Self-Refine** (если все 3 слабые): пересгенерировать с критикой судьи как feedback. Максимум 2 refine-итерации, дальше показываем самый сильный из имеющихся.

### Шаг 6 — Показать → выбор / отказ

Покажи пользователю **3 варианта отдельными блоками** (не одной портянкой). Для каждого:

- `big_idea` (фраза)
- `full_description` (2-3 предложения)
- 3 pillars
- voice + archetype
- (по желанию) validation score

Спроси: **«какой ближе?»** — без вариантов «все плохо» в начале. Если пользователь отказывается от всех — собрать `rejection_reasons` («слишком агрессивный», «не моя ЦА», «звучит как реклама») и:

- 1-й отказ → regenerate с учётом причин
- 2-й отказ → regenerate ещё раз
- 3-й отказ → предложить **expert-fallback** (см. ниже)

### Шаг 7 — Финализировать

После выбора:

- **Если выбран один из вариантов** → можно предложить **refine** под подсказку («тон спокойнее», «добавь конкретную цифру», «убрать агрессию»). Промпт — [`prompts/refine.md`](prompts/refine.md). Refine ≠ sanitize: ядро сохраняется.
- **Если refine не нужен** → финальный артефакт готов.
- **Если 3+ отказа и expert-fallback** → собери expert-артефакт без big_idea:

```json
{
  "track": "expert",
  "big_idea": null,
  "expert_role": "Архитектор с 15 лет опыта",
  "expert_credentials": ["3-5 фактов: годы, проекты, награды, публикации"],
  "voice": "professional",
  "archetype": "Sage",
  "pillars": ["мягкие messaging pillars, не концепт-пилары"]
}
```

## Anti-slop — обязательная гигиена

В [`references/anti-patterns.md`](references/anti-patterns.md) — blacklist из ~30 фраз («премиальное качество», «индивидуальный подход», «лучший на рынке» и т.д.) и brand-swap test. **Любой концепт, содержащий хоть одну фразу из blacklist — автоматически отбраковка.**

Сильный концепт может звучать «не так как все» — это нормально. Не путай **дерзость с AI slop**: дерзкий концепт проходит 11 критериев, slop — не проходит ни одного из 5-7-8-9-10-11.

## Артефакты на выходе

После завершения скилла у пользователя должно быть на руках:

1. **Финальный концепт** (concept-track или expert-track) в структурированном виде — JSON-блок выше.
2. **History** — 2 отвергнутых варианта + причины (часто полезно для будущих коммуникаций — там подсказки что НЕ говорить).
3. **Готовность к downstream** — концепт прямо переиспользуется в Hero-копирайте, About, voice gaид, дизайн-направлении, питч-deck.

## Файлы скилла

**References** (методология — Claude читает по запросу):

- [`references/methodology.md`](references/methodology.md) — что такое хай-концепт, 3 опоры, формулы (Сульянов, StoryBrand, Hollywood)
- [`references/questionnaire.md`](references/questionnaire.md) — 6 блоков интервью + правила проведения
- [`references/validation.md`](references/validation.md) — 11 критериев + scoring + brand-swap test
- [`references/archetypes.md`](references/archetypes.md) — 12 Jungian архетипов + voice + design tokens
- [`references/examples.md`](references/examples.md) — 30+ эталонных концептов (мировые + русскоязычные + продуктовые + кино)
- [`references/anti-patterns.md`](references/anti-patterns.md) — antiпримеры, anti-slop blacklist, brand-swap test

**Prompts** (готовые LLM-промпты — копируй как system):

- [`prompts/interview-system.md`](prompts/interview-system.md) — system prompt для интервью
- [`prompts/divergent.md`](prompts/divergent.md) — генерация одного варианта (personal brand), параметр `angle`
- [`prompts/divergent-product.md`](prompts/divergent-product.md) — генерация для product/service brand
- [`prompts/judge.md`](prompts/judge.md) — LLM-судья по 11 критериям
- [`prompts/refine.md`](prompts/refine.md) — refine выбранного варианта под подсказку

**Examples** — два примера прогонов end-to-end:

- [`examples/personal-coach.md`](examples/personal-coach.md) — фитнес-коуч, personal brand
- [`examples/product-saas.md`](examples/product-saas.md) — нишевый SaaS, product brand

## Gotchas

- **Self-selection: пользователь сразу просит expert-fallback.** Не дави концептом, но скажи: «концепт обычно даёт ×2-3 к эффективности коммуникаций — точно хотите экспертную фактуру?». Если да — короткий путь.
- **Divergent с T=0.85** может давать странные варианты — judge отбраковывает.
- **Self-Refine ≥ 2 итерации = diminishing returns.** После 2-го refine — safe degradation: показываем самый сильный из имеющихся, даже если не идеален.
- **Brand-swap test** для product — критичен. «Надёжное решение для вашего бизнеса» → подставимо под любого конкурента → SLOP. «CRM для автосервисов 5-20 мест без абонплаты» → не подставимо → не slop.
- **Пользователь говорит «все нравятся» на все 3** — редко, но бывает. Форсим выбор: «какой бы вы написали в первый экран сайта?».
- **Концепт ≠ tagline.** Big_idea часто звучит как фраза, но концепт это и pillars, и voice, и enemy, и archetype — это система, а не строчка.
- **Без brief нельзя.** Если пользователь приходит со словами «сделай мне крутой концепт» и не даёт никакого контекста — обязательно проведи интервью. Концепт нельзя выдумать в кабинете, его «добывают» из речи аудитории и реальных отличий.

## Cost / budget

При использовании Claude API:

- Интервью — 6-12 вызовов × ~2K input + ~500 output ≈ 15-30K total tokens
- Divergent — 3 параллельных × ~3K input + ~500 output ≈ 10K
- Judge — 3 × ~2K input + ~200 output ≈ 6.5K
- Self-Refine (если нужен) — +×2 на refinement round

**Total максимум на один концепт** ≈ 50-70K tokens (≈ $0.30-0.50 на Claude Opus с prompt caching включённым).

**Prompt caching обязателен** на system-prompt'ах ≥1K токенов — экономит 90% на повторах. Без caching стоимость ×3-5.

## Источники

См. секцию «Sources» в [`references/methodology.md`](references/methodology.md). Главные:

- Анатолий Сульянов — методология «High-Concept как основа бизнеса» (3 опоры + 11 критериев)
- Donald Miller — *Building a StoryBrand* (2017) — BrandScript / One-Liner
- April Dunford — *Obviously Awesome* (2019) — positioning canvas
- Alex Osterwalder — *Value Proposition Design* (2014) — jobs/pains/gains
- Chip & Dan Heath — *Made to Stick* (2007) — SUCCESs
- Carol S. Pearson — *The Hero Within* (1986) — архетипы
- arXiv 2303.17651 — *Self-Refine: Iterative Refinement with Self-Feedback*
