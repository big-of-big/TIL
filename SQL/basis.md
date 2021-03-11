# SQLの基本
`name age money`をカラムに持つ`users`テーブルを想定

## SELECT
```
SELECT name, money
FROM users
WHERE money > 200000
```

## INSERT
```
INSERT INTO users
VALUES ('lamp', 25, 300000) # カラムの順に書く
```

## UPDATE
```
UPDATE users
SET age = 30
WHERE name = 'lamp'
```

## DELETE
```
DELETE FROM users
WHERE name = 'lamp'
