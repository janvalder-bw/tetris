# tetris

## Assessment: Cloud vs. couch

**cursor_auto.html** — Built by Cursor’s remote models, agents, and a clear spec. The kind of Tetris that actually runs, respects “black and white only,” and doesn’t forget to spawn the first block. The result of something that can read your prompt, plan, and fix its own mistakes. Boringly competent.

**local_qwen_2.5_coder_14B.html** — Built by one untuned model in LM Studio, no agent, no safety net. The kind of Tetris where you half expect the first piece to be a shrug emoji. Proof that 14B parameters on your machine can *almost* hold the whole task in context, then confidently forget to call `newTetromino()` until you yell at it. Charmingly optimistic; occasionally wrong in the most relatable way.

*TL;DR: Cursor = “it just works.” Local = “it *could* work, and we love it anyway.”*