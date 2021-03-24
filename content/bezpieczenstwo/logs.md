---
title: "Logowanie aktywności"
order: 9
---

# Logi, logi i jeszcze raz logi

Każdy spotkał się tym terminem: logi... Ile razy słyszeliśmy od służb IT: "Czekaj... sprawdzę w logach!". Ale co to właściwie są te logi? Po co się je tworzy i jak wykorzystuje?

Zapisywanie czynności dokonywanych przez wszystkich użytkowników jest bardzo ważne. Musimy pamiętać, że nie każdy użytkownik ma tak dobre zamiary jak Ty czy ja 👼. Nie każdy tez musi pamiętać, kiedy i co wykonał w aplikacji.

Każda istotna czynność użytkowania jest zapisywana w bazie i w razie wątpliwości, sporów, czy po prostu konieczności odtworzenia przebiegu aktywności użytkownika, można za pomocą tych danych przygotować obiektywną informację. Typowy log (jeden zapis w basie) zawiera:

- informację o zalogowanym użytkowniku (login),
- rodzaju czynności(np. wysłanie wniosku),
- czas :hourglass: wykonania czynności,
- inne dane.

# Zapisujemy logi

W naszej aplikacji (baza MongoDB) także zapisujemy, kto, co, kiedy... W przypadku wątpliwości możemy sięgnąć po te dane i kiedy zajdzie taka potrzeba przygotować odpowiednią informację.
