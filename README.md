# Dashboard de Recursos Humanos — Power BI
<img width="901" height="503" alt="image" src="https://github.com/user-attachments/assets/f9d82b6c-fd23-4ea2-9104-abc5ab93dcfe" />

## Sobre o Projeto

Este projeto apresenta um **Dashboard interativo de Recursos Humanos**, desenvolvido em **Power BI**, utilizando dados disponibilizados pelo **Data Science Academy**.  
O objetivo é fornecer uma visão estratégica sobre os colaboradores e apoiar decisões nas áreas de gestão de pessoas.

O dashboard permite analisar:

- Demografia da força de trabalho  
- Nível de satisfação  
- Performance dos colaboradores  
- Distribuição por função  
- Tempo de empresa  
- Indicadores financeiros  
- Estado civil  
- Engajamento  

---

## Fonte dos Dados

Os dados utilizados foram obtidos a partir do **Data Science Academy** e incluem variáveis como:

- Gênero  
- Total de funcionários  
- Avaliação de performance  
- Nível de satisfação  
- Anos de experiência na empresa  
- Salário mensal  
- Estado civil  
- Função exercida  

Esses dados serviram como base para a criação dos KPIs e visualizações do dashboard.

---

## Definição dos KPIs

### 1. Indicadores Demográficos
- Total de funcionários  
- Distribuição por gênero  

### 2. Indicador Financeiro
- Média salarial  

### 3. Indicador de Experiência
- Média de anos de experiência na empresa  

### 4. Distribuição por Função
- Percentual de funcionários por cargo  

### 5. Satisfação dos Funcionários
- Classificação do nível de satisfação  

### 6. Engajamento
- Relação entre satisfação e desempenho  

### 7. Estado Civil
- Distribuição por estado civil  

---

## Tratamento dos Dados (Power Query)

### 1. Tabela `Nivel_satisfação_trabalho`

Substituição dos valores numéricos:

| Valor Original | Novo Valor               |
|----------------|---------------------------|
| 1              | Insatisfeito              |
| 2              | Pouco satisfeito          |
| 3              | Moderadamente satisfeito  |
| 4              | Muito satisfeito          |

### 2. Tabela `Aval_performance`

Substituição dos valores numéricos:

| Valor Original | Novo Valor |
|----------------|------------|
| 1              | Ruim       |
| 2              | Baixo      |
| 3              | Médio      |
| 4              | Alto       |

---

## Medidas DAX Criadas

### Contagens

```DAX
TotalFuncionario = COUNTROWS(DatasetRH)

TotalMasculino =
CALCULATE(
    COUNTROWS(DatasetRH),
    DatasetRH[Genero] = "Masculino"
)

TotalFeminino =
CALCULATE(
    COUNTROWS(DatasetRH),
    DatasetRH[Genero] = "Feminino"
)
```

### Percentuais

```DAX
%Homens = DIVIDE([TotalMasculino], [TotalFuncionario], 0)
%Mulheres = DIVIDE([TotalFeminino], [TotalFuncionario], 0)
```

### Médias

```DAX
MédiaAnoExperiencia = AVERAGE(DatasetRH[Anos_na_Empresa])
MédiaSalarial = AVERAGE(DatasetRH[Salario_Mensal])
```

---

## Construção do Dashboard

### Tipos de Gráficos Utilizados

- **Gráficos de Rosca e Pizza**  
  Para indicadores com poucos dados, facilitando a leitura rápida.

- **Gráficos de Faixa e Tabelas**  
  Para comparações e análises distribuídas (por função, satisfação, performance etc.).

- **Cartões (Cards)**  
  Para métricas principais como:
  - Total de funcionários  
  - Média salarial  
  - Média de anos de experiência  

### Paleta de Cores

A paleta utilizada foi composta por **tons frios**:

- Azul  
- Vermelho  
- Roxo  

Escolhidos para proporcionar harmonia e conforto visual.

---

##  Resultado Final

O dashboard final oferece uma visualização clara e objetiva da força de trabalho, permitindo:

- Identificar tendências e padrões  
- Avaliar satisfação e performance  
- Analisar salários e experiência média  
- Entender o perfil dos colaboradores  
- Apoiar decisões estratégicas em RH  

O resultado combina **estética moderna**, **clareza visual** e **eficiência analítica**.

---

## Estrutura do Repositório

```bash
/
├── README.md
├── DashboardRH.pbix
└── assets/
    ├── capa-dashboard.png
    └── imagens-do-dashboard/
```

- `README.md`: Documentação do projeto  
- `DashboardRH.pbix`: Arquivo do dashboard em Power BI  
- `assets/`: Pasta com imagens utilizadas no repositório  

---

## Como Usar

1. Faça o download ou clone este repositório:
   ```bash
   git clone https://github.com/KarenGbm/Dashboard-Recursos-Humanos-Power-BI.git
   ```
2. Abra o arquivo `DashboardRH.pbix` no **Power BI Desktop**.  
3. Explore as visualizações, interaja com os filtros e segmentações.  
4. (Opcional) Conecte outros datasets de RH para expandir as análises.

---

## Tecnologias Utilizadas

- **Power BI Desktop**  
- **Power Query** (ETL e tratamento de dados)  
- **DAX (Data Analysis Expressions)**  
- **Dataset de RH — Data Science Academy**

---

## Autor

- **Seu Nome** — Analista de Dados / Entusiasta de BI  
- LinkedIn:(https://www.linkedin.com/in/karen-guimarães-benedicto-monteiro-db)

---

## Contribuições

Contribuições são bem-vindas!  

Se quiser sugerir melhorias:

1. Faça um **fork** do projeto  
2. Crie uma **branch** para sua feature (`git checkout -b minha-feature`)  
3. Faça o **commit** (`git commit -m "Minha nova feature"`)  
4. Envie para o repositório (`git push origin minha-feature`)  
5. Abra um **Pull Request**

---

## Licença

Este projeto está sob a licença **MIT**.  
Sinta-se à vontade para utilizar, modificar e compartilhar, desde que mantida a referência ao autor original.
