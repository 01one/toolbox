## Run Simple Server

```bash
python3 -m http.server
```
on specific port
```bash
python -m http.server 8000
```

## Create `requirements.txt`

1. Install `pipreqs`:

    ```bash
    pip install pipreqs
    ```

2. Generate `requirements.txt`:

    ```bash
    pipreqs .
    ```

3. If `requirements.txt` already exists and needs to be overwritten:

    ```bash
    pipreqs . --force
    ```
