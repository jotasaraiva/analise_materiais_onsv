library(tidyverse)

df <- read_csv("data (5).csv", col_names = c("dates","user1","atv")) |> 
  separate(
    dates,
    into = c("date_dw", "time"),
    sep = " - "
  ) |> 
  separate(
    user1,
    into = c("user1","org"),
    sep = " - "
  ) |>
  separate(
    atv,
    into = c("atv","obj","dest","user2"),
    sep = ","
  ) |> 
  filter(
    grepl("(cliente)", atv)
  ) |> 
  select(-dest, -user2) |> 
  separate(
    obj,
    into = c("obj1","obj2","obj3","obj4","obj5"),
    remove = FALSE
  ) |> 
  mutate(
    date_up = str_extract(obj, "\\d{4}"),
    date_up2 = str_extract(obj, "\\d{2}"),
    date_up = if_else(is.na(date_up), paste0(20,date_up2), date_up)
  )

view(df)
