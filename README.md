# Github-Actions


1. Create yml file in ```.github/workflows``` directory 

2. Write in your yml file: 
```yaml
name: learn-github-actions
run-name: ${{ github.actor }} is learning GitHub Actions
on: [push]
jobs:
  deploy:
    runs-on: ubuntu-latest

    strategy:
      matrix: 
        node-version: [ 16.x ]

    steps:
      - uses: actions/checkout@v3
      - name: Use Node.js ${{ matrix.node-version }}
        uses: actions/setup-node@v3
        with:
          node-version: ${{ matrix.node-version }}
      - name: install modules
        run: npm install
      - name: build project 
        run: npm run build  
```

3. Setup ssh keys
```bash
ssh-keygen -m PEM -t rsa -b 4096 -C "your-name-github-secret"
```

4. Copy private key in Github repository secrets with ```your-name```

5. Copy public key in .ssh/authorized_keys 
