## Run Simple Server

```
python3 -m http.server
```
on specific port
```
python -m http.server 8000
```

## Create `requirements.txt`

1. Install `pipreqs`:

    ```
    pip install pipreqs
    ```

2. Generate `requirements.txt`:

    ```
    pipreqs .
    ```

3. If `requirements.txt` already exists and needs to be overwritten:

    ```
    pipreqs . --force
    ```
