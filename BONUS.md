BONUS: Using the CLI for Kubernetes diagnostics
----------------------------------------------

How this helps
~~~~~~~~~~~~~~
A local Ollama-based CLI can be useful when diagnosing Kubernetes deployments by:

- Summarizing logs: `kubectl logs` output can be fed to the model to get a concise summary or likely root causes.
- Crafting troubleshooting commands and kubectl manifests based on the observed symptoms.
- Parsing resource descriptions (`kubectl describe`) and pointing out suspicious events.

Suggested additional functionality
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
- An option to accept input from stdin so `kubectl` outputs can be piped directly.
- Helpers to automatically run `kubectl get pods -o wide` and summarize the cluster state.
- Auth-aware execution: fetch cluster context and only run diagnostics in a safe, read-only mode.
- Rate-limiting and size limits: `kubectl` outputs can be huge; the CLI should truncate and summarize before sending to the model.

Simulated interaction
~~~~~~~~~~~~~~~~~~~~~
$ kubectl logs my-app-12345 | python -m ai_cli run --model llama3.2 - \
    --prompt "Summarize the likely cause of the crash and suggested next steps"

(The CLI would receive logs from stdin, send a trimmed version to the model, and print a concise summary and recommended commands such as `kubectl describe pod` or `kubectl exec` troubleshooting steps.)
