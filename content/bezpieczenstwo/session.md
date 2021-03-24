---
title: "Sesja po zalogowaniu"
order: 3
---

# Co to jest sesja?
Jest to stan, z którym związane jest przetrzymywanie danych, ale po stronie serwera - czyli nie na komputerze użytkownika.
Sesja jest identyfikowana najczęściej poprzez ciasteczko, w którym zapisany zostaje id sesji po zalogowaniu.
Serwer odnajduje u siebie odpowiednią sesje po id i dopiero z niej odczytuje lub zapisuje
wrażliwe dane, jak np. id użytkownika. Klient nie ma bezpośredniego dostępu do danych
sesji, które są niejawne i w pewnym sensie bezpieczne.
Sesja w zależności od serwera może zostać stworzona natychmiast lub po pierwszym wpisie
do niej, można to stwierdzić podglądając ciasteczka w przeglądarce.

---

# Powyższy mechanizm wykorzystujemy w slaskietalenty.com
Powyższy sposób przechowywania danych po zalogowaniu w dużym stopniu wpływa na bezpieczeństwo. Powszechnie wykorzystuje się i inne strategie (jak np. JWT), ale uważa się, że przechowywanie danych logowania w sesji i powiązanych z nią ciasteczek jest najbezpieczniejszy.
