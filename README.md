Codigo lenguaje M:

let
    Origen = Csv.Document(File.Contents("C:\Users\juanc\OneDrive\Escritorio\dataset_ventas_lacteos_2024.csv"),[Delimiter=",", Columns=14, Encoding=65001, QuoteStyle=QuoteStyle.None]),
    #"Encabezados promovidos" = Table.PromoteHeaders(Origen, [PromoteAllScalars=true]),
    #"Tipo cambiado" = Table.TransformColumnTypes(#"Encabezados promovidos",{{"ID Orden", Int64.Type}, {"Fecha", type date}, {"Nombre del vendedor", type text}, {"Nombre del supermercado", type text}, {"Representante de compras", type text}, {"Estado", type text}, {"Ciudad", type text}, {"Categoría", type text}, {"Producto", type text}, {"Presentación", type text}, {"Precio unitario (USD)", Int64.Type}, {"Cantidad comprada", Int64.Type}, {"Valor total (USD)", Int64.Type}, {"Forma de pago", type text}}),
    #"Duplicados quitados" = Table.Distinct(#"Tipo cambiado", {"ID Orden"}),
    #"Filas filtradas" = Table.SelectRows(#"Duplicados quitados", each ([ID Orden] <> null) and ([Ciudad] = "Rochester")),
    #"Valor reemplazado" = Table.ReplaceValue(#"Filas filtradas","","Nueva York",Replacer.ReplaceValue,{"Estado"}),
    #"Mi transformacion manual" = Table.RenameColumns(#"Valor reemplazado",{{"Fecha", "Fecha de venta"}}), //cambio el nombre del paso que utilice para cambiar el nombre de la columna de fecha a fecha de venta para identificar mejor. Luego la referencie en la siguiente linea.
    #"Tipo cambiado1" = Table.TransformColumnTypes(#"Mi transformacion manual",{{"Precio unitario (USD)", Currency.Type}, {"Valor total (USD)", Currency.Type}})
in
    #"Tipo cambiado1"

¿Por qué es útil para un analista de datos entender la estructura let … in?
Entender la estructura let - in me permite identificar posibles errores, modificar lineas mas facilmente e incluso realizar funciones personalizadas que no existe de manera estandar.

¿Qué significa que el lenguaje M sea Case Sensitive y cuál es la consecuencia práctica de ignorarlo?
Significa que el lenguaje M es sensible a mayusculas y minusculas, no saberlo nos hace propensos a errores de codigo. Si no utilizamos las mayusculas correctamente las lineas van a arrojar error.

¿Por qué elegiste ese dataset y qué criterios usaste para seleccionarlo?
Era un dataset gratuito en formato .csv con columnas variadas, numerosos datos pero algunos duplicados o nulos. Bastante ordenado pero habia que hacerle unas pequeñas modificaciones.

Link del dataset: https://www.kaggle.com/datasets/hectorconde/dataset-ventas-lacteos-2024
