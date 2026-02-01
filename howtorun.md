# Running the Gateway

## 1. Kill existing processes

```bash
pkill -9 -f "openclaw-gateway" 2>/dev/null || true
pkill -9 -f "openclaw" 2>/dev/null || true
```

## 2. Build (if needed)

```bash
pnpm build
```

## 3. Start (background, survives terminal disconnect)

```bash
nohup pnpm start gateway --force > /tmp/moltbot-gateway.log 2>&1 &
disown
```

## 4. Check if running

```bash
pgrep -af "openclaw-gateway"
```

Or check the port:

```bash
ss -ltnp | grep 18789
```

## View logs

```bash
tail -f /tmp/moltbot-gateway.log
```

## Stop

```bash
pkill -9 -f "openclaw-gateway"
```

## Troubleshooting

If startup fails, check logs:

```bash
tail -50 /tmp/moltbot-gateway.log
```

List all running processes:

```bash
ps aux | grep -E "openclaw|gateway" | grep -v grep
```
