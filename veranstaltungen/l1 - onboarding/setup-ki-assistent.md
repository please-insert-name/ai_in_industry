# Setup KI Assistent
*Author*: Mike
*Date*: 2026-01-28
*Date modified*: 2026-02-03
*Category*: AI
*Keywords*: Ollama, Claude Code, VS Code
*Level*: [ ] basic, [x] advanced, [ ] expert

## Summary
Es wird gezeigt, wie man mit Ollama und Claude Code einen lokalen Assistenten für VS Code aufsetzen kann. Im Beispiel wird ein Ollama-Server im Intranet angesprochen. Es ist auch ein lokaler Ollama-Server möglich.

## Usage
- CMD-Shell im Arbeitsverzeichnis öffnen
- VS Code starten
```
> code .
```
- Claude Code in Shell starten
```
> claude --model glm-4.7-flash:latest
```
- Alternativ: Mit Ollama Cloud Modell starten
```
> ollama pull kimi-k2.5:cloud  # einmalig fuer Manifest
> claude --model kimi-k2.5:cloud
```

## Content
Siehe hierzu auch:
https://exploringartificialintelligence.substack.com/p/how-to-run-claude-code-with-ollama

### Schritt 1: Installiere Ollama
Ollama downloaden und installieren (erforderlich: V0.15.0+)
https://ollama.com/
(nicht erforderlich, wenn ein Remote Ollama Server verwendet wird.)

Bei lokaler Installation: Geeignetes Modell herunterladen, bspw.
```
ollama pull glm-4.7-flash:latest
```

Lokales Modell testen
```
ollama run glm-4.7-flash:latest
```

### Optional: Remote Ollama Server als lokalen default
Wenn Ollama lokal installiert ist, kann man den Zielserver per Umgebungsvariable ändern.
Umgebungsvariable:
```
set OLLAMA_HOST = http://172.20.1.88:11434
```
Damit wird über Kommandozeile die API des Remote Hosts angesprochen, anstelle localhost.

### Schritt 2: Installiere Claude Code
Für Windows (CMD Shell)
```
curl -fsSL https://claude.ai/install.cmd -o install.cmd && install.cmd && del install.cmd
```

Für Linux
```
curl -fsSL https://claude.ai/install.sh | bash
```

### Schritt 3: Konfiguriere Claude Code für Ollama

Umgebungsvariablen setzen (per session or in windows settings)
```
set ANTHROPIC_AUTH_TOKEN=ollama
set ANTHROPIC_BASE_URL=http://172.20.1.88:11434
```

Testen
```
claude --model glm-4.7-flash:latest
```

### Schritt 4: Claude Code und Ollama Cloud Modelle

- bereits nutzbar mit dem free account
- Registrierung erforderlich auf ollama.com (bspw. mit Google Account)
- Device connecten über Browser
```
ollama signin
```
- Modell-Manifest pullen
```
ollama pull kimi-k2.5:cloud
```
- Claude Code starten mit Ollama Cloud Modell
```
claude --model kimi-k2.5:cloud
```

(For FAQ on Pricing see: https://ollama.com/pricing)

### Beispiel-Anfrage
"""
bitte recherchiere im internet den aktuellen stand zum thema 'llms auf raspberry pi 5 laufen lassen'. analysiere die gefundenen quellen und speichere eine zusammenfassung mit quellenangaben in 'raspi-5-llms-md'
"""

"""
Frage: "Was muss ich beachten, wenn ich ein Überdruckventil an einem Tank für Chlorgas installiere?" Beantworte die Frage anhand der Vorschriften der BAuA. Diese findest du in C:\Users\mkroehn\Projekte\20_Workspace\Projects\PSS-Assistent\markdowns. Einen Überblick findest du in C:\Users\mkroehn\Projekte\20_Workspace\Projects\PSS-Assistent\overview.md. Zur Analyse kannst du auf den dacli-mcp-server zurückgreifen.
"""