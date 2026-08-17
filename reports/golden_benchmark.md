# Lab 17 Golden Set Report

- Implementation: `student`
- Kind: `golden`
- Cases: **20**
- Passed: **20/20**
- Evidence hit rate: **100.0%**
- Average retrieval latency: **952.3 ms**
- Average token reduction vs full source context: **8.7%**
- Golden bonus: **10/10** (100% required)

| Case | Layer | Pass | Latency ms | Retrieved tokens | Token reduction | Missing / Error |
| --- | --- | --- | ---: | ---: | ---: | --- |
| G01 | short_term | PASS | 0.5 | 227 | 0.0% |  |
| G02 | short_term | PASS | 0.2 | 133 | 0.0% |  |
| G08 | long_term | PASS | 1530.6 | 726 | 0.0% |  |
| G09 | long_term | PASS | 1412.6 | 1438 | 0.0% |  |
| G12 | semantic | PASS | 291.8 | 365 | 20.5% |  |
| G14 | semantic | PASS | 252.3 | 217 | 43.9% |  |
| G15 | semantic | PASS | 268.4 | 217 | 52.7% |  |
| G19 | mixed | PASS | 1608.2 | 581 | 0.0% |  |
| G03 | long_term | PASS | 1409.9 | 1430 | 0.0% |  |
| G04 | long_term | PASS | 1386.8 | 1423 | 0.0% |  |
| G05 | long_term | PASS | 1633.1 | 1426 | 0.0% |  |
| G10 | episodic | PASS | 259.0 | 454 | 0.0% |  |
| G11 | episodic | PASS | 260.7 | 454 | 0.0% |  |
| G13 | semantic | PASS | 260.0 | 363 | 35.8% |  |
| G16 | mixed | PASS | 1620.0 | 581 | 0.0% |  |
| G18 | mixed | PASS | 524.4 | 489 | 13.5% |  |
| G20 | mixed | PASS | 1888.9 | 831 | 0.0% |  |
| G06 | long_term | PASS | 1410.4 | 1426 | 0.0% |  |
| G07 | long_term | PASS | 1392.3 | 1429 | 0.0% |  |
| G17 | mixed | PASS | 1635.2 | 581 | 8.1% |  |

## Evidence excerpts

### G01 - short_term

`<SESSION_SUMMARY> user: Constraint HOLD-ALPHA-0900: standup is 09:00 sharp and must not be forgotten. | assistant: Noted standup constraint. | user: Constraint HOLD-BETA-STAGING: writes go to staging DB only. | assistant: Noted staging constraint. | user: Filler A about button padding. | assistant: Filler A. | user: Filler B about color tokens. | assistant: Filler B. | user: Filler C about copy tone. | assistant: Filler C. </SESSION_SUMMARY> <DURABLE_NOTES> - user: Constraint HOLD-ALPHA-0900: standup is 09:00 sharp and must not be forgotten. - assistant: Noted standup constraint. - user: Constraint HOLD-BETA-STAGING: writes go to staging DB only. - assistant: Noted staging constraint. </DURA`

### G02 - short_term

`<RECENT_TURNS> user: Ten du an ca nhan cua toi la ORCHID-27. Toi thich Python va khong thich Java. Khi giai thich code, hay dung vi du ngan. assistant: Da hieu: demo ca nhan ORCHID-27, uu tien Python, tranh Java, vi du ngan. user: Toi dang hoc async/await va hay nham coroutine voi Task. Neu sau nay gap chu de nay, hay giai thich bang timeline. assistant: Toi se uu tien timeline khi giai thich coroutine va Task. user: TODO: hoan thanh benchmark report truoc thu Sau luc 16:00. Day la open loop LAB-REPORT-1600. </RECENT_TURNS>`

### G08 - long_term

`<USER_SUMMARY> Lan Tran's project is LOTUS-88. Lan prioritizes Java and Spring Boot for backend examples and does not use Python for backend examples. </USER_SUMMARY>  <EPISODES> Episodes are source message or document excerpts shown in selection order.   - Created At: 2026-08-01 11:00:00     Source: message     Content: [user] {   "user_id": "lan-lab17",   "first_name": "Lan",   "last_name": "Tran",   "user_alias": "Lan Tran" }: Toi la Lan. Du an cua toi la LOTUS-88. Toi uu tien Java va Spring Boot, va khong dung Python trong vi du backend.   - Created At: 2026-08-01 11:00:20     Source: message     Content: Lab Assistant (assistant): Da hieu: LOTUS-88, Java + Spring Boot cho backend exampl`

### G09 - long_term

`<USER_SUMMARY> Minh Nguyen is working on a personal project called ORCHID-27. For the company project BLUEBIRD-42, the backend must use TypeScript with NestJS, not Python. Minh prefers Python for personal demos like ORCHID-27. Minh has a deadline to complete a benchmark report before Friday at 16:00, which is an open loop task labeled LAB-REPORT-1600. Minh is currently debugging async HTTP requests, investigating connection pool, client lifecycle, and concurrency issues. Minh found that reusing the aiohttp ClientSession and setting concurrency to 20 is an effective solution. The primary issue was identified as connection churn, not the timeout threshold, related to the ASYNC-FIX-20 incident.`

### G12 - semantic

`EPISODE: {"id":"kb-payment-retry","entity":"Payment API Retry Policy","summary":"For POST /payments, every retryable request MUST send the same Idempotency-Key. Retry only HTTP 429 or transient 5xx errors, use exponential-backoff, and stop after max-3-retries. Marker: PAYMENT-RULE-3.","source":"internal-api-guideline-v3","updated_at":"2026-08-10T00:00:00Z"} metadata= EPISODE: For POST /payments, every retryable request MUST send the same Idempotency-Key. Retry only HTTP 429 or transient 5xx errors, use exponential-backoff, and stop after max-3-retries. Marker: PAYMENT-RULE-3. metadata= EPISODE: {"id":"kb-memory-privacy","entity":"Agent Memory Privacy Rule","summary":"Do not persist personal `

### G14 - semantic

`EPISODE: {"id":"kb-memory-privacy","entity":"Agent Memory Privacy Rule","summary":"Do not persist personal data without explicit opt-in. A deletion request must remove user-scoped memory and be verified across every store. Marker: DELETE-VERIFY-ALL.","source":"memory-governance-policy","updated_at":"2026-08-12T00:00:00Z"} metadata= EPISODE: Do not persist personal data without explicit opt-in. A deletion request must remove user-scoped memory and be verified across every store. Marker: DELETE-VERIFY-ALL. metadata= EPISODE: {"id":"kb-context-budget","entity":"Memory Context Budget","summary":"Reserve bounded context for memory. This lab uses short-term 10 percent, long-term 4 percent, episodi`

### G15 - semantic

`EPISODE: {"id":"kb-memory-privacy","entity":"Agent Memory Privacy Rule","summary":"Do not persist personal data without explicit opt-in. A deletion request must remove user-scoped memory and be verified across every store. Marker: DELETE-VERIFY-ALL.","source":"memory-governance-policy","updated_at":"2026-08-12T00:00:00Z"} metadata= EPISODE: Do not persist personal data without explicit opt-in. A deletion request must remove user-scoped memory and be verified across every store. Marker: DELETE-VERIFY-ALL. metadata= EPISODE: {"id":"kb-context-budget","entity":"Memory Context Budget","summary":"Reserve bounded context for memory. This lab uses short-term 10 percent, long-term 4 percent, episodi`

### G19 - mixed

`<LONG_TERM> <USER_SUMMARY> Lan Tran's project is LOTUS-88. Lan prioritizes Java and Spring Boot for backend examples and does not use Python for backend examples. </USER_SUMMARY>  <EPISODES> Episodes are source message or document excerpts shown in selection order.   - Created At: 2026-08-01 11:00:00     Source: message     Content: [user] {   "user_id": "lan-lab17",   "first_name": "Lan",   "last_name": "Tran",   "user_alias": "Lan Tran" }: Toi la Lan. Du an cua toi la LOTUS-88. Toi uu tien Java va Spring Boot, va khong dung Python trong vi du backend.   - Created At: 2026-08-01 11:00:20     Source: message     Content: Lab Assistant (assistant): Da hieu: LOTUS-88, Java + Spring Boot cho ba`

### G03 - long_term

`<USER_SUMMARY> Minh Nguyen is working on a personal project called ORCHID-27, for which they prefer using Python. For the company project BLUEBIRD-42, the backend must use TypeScript with NestJS, not Python. Minh is currently debugging async HTTP requests, investigating connection pool, client lifecycle, and concurrency issues. They found that reusing the aiohttp ClientSession and setting concurrency to 20 is an effective solution. The primary issue was identified as connection churn, not the timeout threshold, related to the ASYNC-FIX-20 incident. Minh has a deadline to complete a benchmark report before Friday at 16:00.  Minh Nguyen prefers Python and dislikes Java. They want code explanat`

### G04 - long_term

`<USER_SUMMARY> Minh Nguyen is working on a personal project called ORCHID-27, for which they prefer using Python. For the company project BLUEBIRD-42, the backend must use TypeScript with NestJS, not Python. Minh is currently debugging async HTTP requests, investigating connection pool, client lifecycle, and concurrency issues. They found that reusing the aiohttp ClientSession and setting concurrency to 20 is an effective solution. The primary issue was identified as connection churn, not the timeout threshold, related to the ASYNC-FIX-20 incident. Minh has a deadline to complete a benchmark report before Friday at 16:00.  Minh Nguyen prefers Python and dislikes Java. They want code explanat`

### G05 - long_term

`<USER_SUMMARY> Minh Nguyen is working on a personal project called ORCHID-27, for which they prefer using Python. For the company project BLUEBIRD-42, the backend must use TypeScript with NestJS, not Python. Minh is currently debugging async HTTP requests, investigating connection pool, client lifecycle, and concurrency issues. They found that reusing the aiohttp ClientSession and setting concurrency to 20 is an effective solution. The primary issue was identified as connection churn, not the timeout threshold, related to the ASYNC-FIX-20 incident. Minh has a deadline to complete a benchmark report before Friday at 16:00.  Minh Nguyen prefers Python and dislikes Java. They want code explanat`

### G10 - episodic

`EPISODE: Ten du an ca nhan cua toi la ORCHID-27. Toi thich Python va khong thich Java. Khi giai thich code, hay dung vi du ngan. EPISODE: Da hieu: demo ca nhan ORCHID-27, uu tien Python, tranh Java, vi du ngan. EPISODE: Toi dang hoc async/await va hay nham coroutine voi Task. Neu sau nay gap chu de nay, hay giai thich bang timeline. EPISODE: Toi se uu tien timeline khi giai thich coroutine va Task. EPISODE: TODO: hoan thanh benchmark report truoc thu Sau luc 16:00. Day la open loop LAB-REPORT-1600. EPISODE: Hom nay toi debug async HTTP. Toi da thu tang timeout len 60s nhung van fail. EPISODE: Hay kiem tra connection pool, lifecycle cua client va concurrency. EPISODE: Cach hieu qua la reuse a`

### G11 - episodic

`EPISODE: Ten du an ca nhan cua toi la ORCHID-27. Toi thich Python va khong thich Java. Khi giai thich code, hay dung vi du ngan. EPISODE: Da hieu: demo ca nhan ORCHID-27, uu tien Python, tranh Java, vi du ngan. EPISODE: Toi dang hoc async/await va hay nham coroutine voi Task. Neu sau nay gap chu de nay, hay giai thich bang timeline. EPISODE: Toi se uu tien timeline khi giai thich coroutine va Task. EPISODE: TODO: hoan thanh benchmark report truoc thu Sau luc 16:00. Day la open loop LAB-REPORT-1600. EPISODE: Hom nay toi debug async HTTP. Toi da thu tang timeout len 60s nhung van fail. EPISODE: Hay kiem tra connection pool, lifecycle cua client va concurrency. EPISODE: Cach hieu qua la reuse a`

### G13 - semantic

`EPISODE: {"id":"kb-async-http","entity":"Async HTTP Incident Playbook","summary":"When async HTTP calls time out, inspect connection pooling, downstream saturation and concurrency before increasing timeout. Reuse a long-lived client session where possible. Marker: CONN-POOL-FIRST.","source":"incident-playbook-2026","updated_at":"2026-08-11T00:00:00Z"} metadata= EPISODE: When async HTTP calls time out, inspect connection pooling, downstream saturation and concurrency before increasing timeout. Reuse a long-lived client session where possible. Marker: CONN-POOL-FIRST. metadata= EPISODE: {"id":"kb-memory-privacy","entity":"Agent Memory Privacy Rule","summary":"Do not persist personal data witho`

### G16 - mixed

`<LONG_TERM> <USER_SUMMARY> Minh Nguyen is working on a personal project called ORCHID-27, for which they prefer using Python. For the company project BLUEBIRD-42, the backend must use TypeScript with NestJS, not Python. Minh is currently debugging async HTTP requests, investigating connection pool, client lifecycle, and concurrency issues. They found that reusing the aiohttp ClientSession and setting concurrency to 20 is an effective solution. The primary issue was identified as connection churn, not the timeout threshold, related to the ASYNC-FIX-20 incident. Minh has a deadline to complete a benchmark report before Friday at 16:00.  Minh Nguyen prefers Python and dislikes Java. They want c`

### G18 - mixed

`<EPISODIC> EPISODE: Ten du an ca nhan cua toi la ORCHID-27. Toi thich Python va khong thich Java. Khi giai thich code, hay dung vi du ngan. EPISODE: Da hieu: demo ca nhan ORCHID-27, uu tien Python, tranh Java, vi du ngan. EPISODE: Toi dang hoc async/await va hay nham coroutine voi Task. Neu sau nay gap chu de nay, hay giai thich bang timeline. EPISODE: Toi se uu tien timeline khi giai thich coroutine va Task. EPISODE: TODO: hoan thanh benchmark report truoc thu Sau luc 16:00. Day la open loop LAB-REPORT-1600. EPISODE: Hom nay toi debug async HTTP. Toi da thu tang timeout len 60s nhung van fail. EPISODE: Hay kiem tra connection pool, lifecycle cua client va concurrency. EPISODE: Cach hieu qua`

### G20 - mixed

`<LONG_TERM> <USER_SUMMARY> Minh Nguyen is working on a personal project called ORCHID-27, for which they prefer using Python. For the company project BLUEBIRD-42, the backend must use TypeScript with NestJS, not Python. Minh is currently debugging async HTTP requests, investigating connection pool, client lifecycle, and concurrency issues. They found that reusing the aiohttp ClientSession and setting concurrency to 20 is an effective solution. The primary issue was identified as connection churn, not the timeout threshold, related to the ASYNC-FIX-20 incident. Minh has a deadline to complete a benchmark report before Friday at 16:00.  Minh Nguyen prefers Python and dislikes Java. They want c`

### G06 - long_term

`<USER_SUMMARY> Minh Nguyen is working on a personal project called ORCHID-27, for which they prefer using Python. For the company project BLUEBIRD-42, the backend must use TypeScript with NestJS, not Python. Minh is currently debugging async HTTP requests, investigating connection pool, client lifecycle, and concurrency issues. They found that reusing the aiohttp ClientSession and setting concurrency to 20 is an effective solution. The primary issue was identified as connection churn, not the timeout threshold, related to the ASYNC-FIX-20 incident. Minh has a deadline to complete a benchmark report before Friday at 16:00.  Minh Nguyen prefers Python and dislikes Java. They want code explanat`

### G07 - long_term

`<USER_SUMMARY> Minh Nguyen is working on a personal project called ORCHID-27, for which they prefer using Python. For the company project BLUEBIRD-42, the backend must use TypeScript with NestJS, not Python. Minh is currently debugging async HTTP requests, investigating connection pool, client lifecycle, and concurrency issues. They found that reusing the aiohttp ClientSession and setting concurrency to 20 is an effective solution. The primary issue was identified as connection churn, not the timeout threshold, related to the ASYNC-FIX-20 incident. Minh has a deadline to complete a benchmark report before Friday at 16:00.  Minh Nguyen prefers Python and dislikes Java. They want code explanat`

### G17 - mixed

`<LONG_TERM> <USER_SUMMARY> Minh Nguyen is working on a personal project called ORCHID-27, for which they prefer using Python. For the company project BLUEBIRD-42, the backend must use TypeScript with NestJS, not Python. Minh is currently debugging async HTTP requests, investigating connection pool, client lifecycle, and concurrency issues. They found that reusing the aiohttp ClientSession and setting concurrency to 20 is an effective solution. The primary issue was identified as connection churn, not the timeout threshold, related to the ASYNC-FIX-20 incident. Minh has a deadline to complete a benchmark report before Friday at 16:00.  Minh Nguyen prefers Python and dislikes Java. They want c`
