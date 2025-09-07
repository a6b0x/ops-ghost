```bash
cd dataflow
sdf run --ui --port 8888
show state count-words/count-per-word/state

fluvio produce sentences -f sentences.txt
fluvio produce words -f words.txt
fluvio consume sentences -Bd
fluvio consume words -Bd

```