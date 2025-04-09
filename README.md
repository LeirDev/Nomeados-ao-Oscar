# Nomeados ao Oscar

Contém a base de indicados ao Oscar em formato SQL para treinar comandos CRUD. 

Abaixo, algumas atividades para trabalharmos.

--- 

* Atualize os registros da tabela com os dados do Oscar 2025
  
  R: Dados atualizados e inseridos no banco de dados.
  
---

* Qual o **total** de registros na tabela indicados?

R: 11004

Q: 
```js
db.registros.countDocument()
```
---

* Qual o número de indicações por categoria agrupadas por categoria?

R: 2

Q:
```js
db.indicados_ao_oscar.aggregate([
  {
    $group: {
      _id: "$categoria",  
      total_indicacoes: { $sum: 1 }  
    }
  },
  {
    $sort: { total_indicacoes: -1 } 
  }
]);
```

---

* Quantas vezes Natalie Portman foi indicada ao Oscar?

R: 3 vezes

Q:
```js
 db.oscar.find({"Nome": "Natalie Portman"}).countDocuments()
```

---

* Quantos Oscars Natalie Portman ganhou?

R: 1 oscar

Q:
```js
 db.registros.find({
"nome_do_indicado": "Natalie Portman", "vencedor": "true"
})
```
---

* Quantas vezes Viola Davis foi indicada ao Oscar?
  
R: 4 vezes

Q:
```js
 db.oscar.find({"Nome": "Natalie Portman"}).countDocuments()
```
---

* Quantos Oscars Viola Davis ganhou?

R: 1 vez

Q:
```js
 db.registros.countDocuments({"nome_do_indicado": "Viola Davis", "vencedor": "true"})
```
---

* Amy Adams já ganhou algum Oscar?

R: 1 vez

Q:
```js
 db.registros.countDocuments({"nome_do_indicado": "Viola Davis", "vencedor": "true"})
```
---

* Quais os atores/atrizes que foram indicados mais de uma vez?

R:
Q: comando para saber quantos foram indicados mais de uma vez:
```js
 db.registros.aggregate([
  { $group: { _id: "$nome_do_indicado", total_indicacoes: { $sum: 1 } } },
  { $match: { total_indicacoes: { $gt: 1 } } },
  { $count: "quantidade_atores_mais_uma_indicacao" }
])
``` 

Q: Comando para saber nome e quantidade dos atores indicados mais de uma vez:
```js
 db.registros.aggregate([
  { $group: { _id: "$nome_do_indicado", total_indicacoes: { $sum: 1 } } },
  { $match: { total_indicacoes: { $gt: 1 } } }
])
``` 
---

* A série de filmes Toy Story ganhou Oscars em quais anos?


---

* A partir de que ano que a categoria "Actress" deixa de existir? 

---

* Quem ganhou o primeiro Oscar para Melhor Atriz? Em que ano?

---

* Na campo "Vencedor", altere todos os valores com "true" para 1 e todos os valores "false" para 0.

---

* Em qual edição do Oscar "Crash" concorreu ao Oscar?

---

* O filme Central do Brasil aparece no Oscar?

---

* Inclua no banco 3 filmes que nunca foram nem nomeados ao Oscar, mas que merecem ser. 

---

* Denzel Washington já ganhou algum Oscar?

---

* Quais os filmes que ganharam o Oscar de Melhor Filme?

---

* Sidney Poitier foi o primeiro ator negro a ser indicado ao Oscar. Em que ano ele foi indicado? Por qual filme?

---

* Quais os filmes que ganharam o Oscar de Melhor Filme e Melhor Diretor na mesma cerimonia?

---

* Denzel Washington e Jamie Foxx já concorreram ao Oscar no mesmo ano?
