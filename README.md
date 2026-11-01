# Projeto_Ada_Analise_Vendas_Supermercado[analise_vendas2.py](https://github.com/user-attachments/files/34242470/analise_vendas2.py)
import pandas as pd

df = pd.read_csv("vendas_supermercado_com_cliente.csv")

df ["Data"] = pd.to_datetime(df["Data"])

df["Mes"] = df["Data"].dt.month

df["Dia_Semana"]=df["Data"].dt.day_name()

print(df["Categoria"].unique())


print(
    df.groupby(["Categoria", "Mes"])["Quantidade"].sum()
)

resultado = df.groupby(["Categoria", "Mes"])["Quantidade"].sum()



print(
    df.groupby("Categoria")["Quantidade"]
      .sum()
      .sort_values(ascending=False)
)

import pandas as pd
df = pd.read_csv("vendas_supermercado_com_cliente.csv")
df["Data"] = pd.to_datetime(df["Data"])
df["Mes"] = df["Data"].dt.month
resultado = (
    df.groupby(["Categoria", "Mes"])["Quantidade"]
    .sum()
    .reset_index()
)
print(resultado.head())

resultado.sort_values(
    by="Quantidade",
    ascending=False
).head(10)

print(
    resultado.sort_values(
        by="Quantidade",
        ascending=False
    ).head(20)
)

media_diaria = (
    df.groupby(["Categoria", "Data"])["Quantidade"]
    .sum()
    .reset_index()
)
print(media_diaria.head())

media_categoria = (
    media_diaria.groupby("Categoria")["Quantidade"]
    .mean()
    .sort_values(ascending=False)
)
print(media_categoria)

sazonalidade = (
    df.groupby(["Produto", "Mes"])["Quantidade"]
    .sum()
    .reset_index()
)
variacao = (
    sazonalidade.groupby("Produto")["Quantidade"]
    .std()
    .sort_values(ascending=False)
)
print(variacao.head(10))

df["Faixa_Etaria"] = pd.cut(
    df["Idade"],
    bins=[18, 35, 59, 100],
    labels=["Jovem", "Adulto", "Idoso"],
    include_lowest=True
)
vendas_faixa = (
    df.groupby("Faixa_Etaria")["Total_Venda"]
    .sum()
    .sort_values(ascending=False)
)
print(vendas_faixa)

relacao_idade_categoria = (
    df.groupby(["Faixa_Etaria", "Categoria"])["Quantidade"]
    .sum()
    .sort_values(ascending=False)
)
print(relacao_idade_categoria)

vendas_dia_semana = (
    df.groupby("Dia_Semana")["Total_Venda"]
    .sum()
    .sort_values(ascending=False)
)
print(vendas_dia_semana)

df["Data"] = pd.to_datetime(df["Data"])
df["Mes"] = df["Data"].dt.month
df["Dia_Semana"] = df["Data"].dt.day_name()

print(df.columns)

df["Dia_Semana"] = df["Data"].dt.day_name()

vendas_dia_semana = (
    df.groupby("Dia_Semana")["Total_Venda"]
    .sum()
    .sort_values(ascending=False)
)
print(vendas_dia_semana)

df["Data"] = pd.to_datetime(df["Data"])
df["Mes"] = df["Data"].dt.month
df["Dia_Semana"] = df["Data"].dt.day_name()
print(df.columns)



