# System zarządzania gabinetami stomatologicznymi - dokumentacja

## Wprowadzenie

System zarządzania gabinetami stomatologicznymi to kompleksowe rozwiązanie dla klinik stomatologicznych, umożliwiające efektywne zarządzanie personelem, pacjentami, wizytami oraz rozliczeniami. System został zaprojektowany w architekturze wielopoziomowej (multi-tenant), co pozwala na obsługę wielu klinik w ramach jednej instancji aplikacji z pełną izolacją danych.

## Architektura systemu

System został zaimplementowany z wykorzystaniem nowoczesnego stosu technologicznego:

- **Backend**: Node.js + NestJS (TypeScript)
- **Frontend**: React + TypeScript
- **Baza danych**: PostgreSQL
- **Cache i logi**: Redis
- **Uwierzytelnianie**: JWT (JSON Web Tokens)
- **Dokumentacja API**: Swagger (OpenAPI)

## Kluczowe funkcjonalności

### 1. System multitenancy

Każda klinika jest niezależnym tenantem (najemcą) w systemie, co zapewnia:
- Pełną izolację danych pomiędzy klinikami
- Możliwość zarządzania wieloma lokalizacjami w ramach jednej kliniki
- Dedykowaną administrację dla każdej kliniki
- Współdzielenie infrastruktury przy zachowaniu bezpieczeństwa danych

### 2. Zarządzanie użytkownikami

- Role systemowe z granularnymi uprawnieniami (Administrator, Kierownik, Menadżer, Recepcjonistka, Lekarz, Asystentka, CallCenter, KierownikMarketingu)
- Przypisanie personelu medycznego do lokalizacji i gabinetów
- Zarządzanie specjalizacjami lekarzy
- System oceny pracowników z konfigurowalnymi kryteriami
- Śledzenie dostępności personelu w różnych lokalizacjach

### 3. Zarządzanie umowami i rozliczeniami

- Obsługa różnych typów umów (o pracę, B2B, zlecenie)
- Definiowanie stawek dla poszczególnych usług i lekarzy
- Okresy obowiązywania stawek z możliwością zmiany w czasie
- Rozliczenia pracowników na podstawie wykonanych usług
- Przechowywanie dokumentacji umów

### 4. System dokumentów i formularzy

- Zarządzanie dokumentami pracowników (umowy, certyfikaty, zaświadczenia)
- Kreator formularzy dla pracowników z konfigurowalnymi polami
- Proces akceptacji i weryfikacji wypełnionych formularzy
- Automatyczne wypełnianie danych formularzy na podstawie danych użytkowników

### 5. Zarządzanie pacjentami i wizytami

- Pełna karta pacjenta z historią wizyt
- Zarządzanie potencjalnymi pacjentami (leads)
- Planowanie i zarządzanie wizytami
- Kalendarz z widokiem dla całej kliniki, lokalizacji lub pojedynczych lekarzy
- Plany leczenia z etapami realizacji
- Automatyczne powiadomienia dla pacjentów i personelu

### 6. Rozliczenia i płatności

- Zarządzanie cennikiem usług
- Obsługa różnych form płatności
- Generowanie faktur i paragonów
- Rabaty i programy lojalnościowe dla pacjentów

### 7. Bezpieczeństwo i audyt

- Pełne logowanie wszystkich zmian w systemie
- Śledzenie dostępu do danych
- Bezpieczne przechowywanie haseł
- Izolacja danych między tenantami
- Kontrola dostępu oparta na rolach i uprawnieniach

## Wdrożenie

System jest gotowy do wdrożenia w środowisku produkcyjnym z wykorzystaniem:

1. **Serwer aplikacyjny**: Node.js z PM2 do zarządzania procesami
2. **Baza danych**: PostgreSQL zgodnie z podanymi parametrami:
   - DB_HOST=localhost
   - DB_PORT=5432
   - DB_USERNAME=mariodb
   - DB_PASSWORD=mariodb123
   - DB_DATABASE=clinic_db
3. **Cache**: Redis do przechowywania sesji i logowania zmian na kontach
4. **Konteneryzacja**: Docker do łatwego wdrożenia całego stosu technologicznego
5. **CI/CD**: Pipeline z automatycznymi testami i wdrożeniami

## Rozszerzalność

System zaprojektowano z myślą o łatwej rozszerzalności:

1. **Moduły**: Architektura modułowa pozwala na łatwe dodawanie nowych funkcjonalności
2. **API**: Pełne REST API umożliwiające integrację z systemami zewnętrznymi
3. **Konfigurowalność**: Możliwość dostosowania systemu do specyficznych potrzeb kliniki
4. **Skalowalność**: Architektura umożliwiająca obsługę od małych gabinetów po duże sieci klinik


# System Zarządzania Klinikami Stomatologicznymi 🦷

Kompleksowy system do zarządzania klinikami stomatologicznymi z architekturą multi-tenant, umożliwiający efektywne zarządzanie personelem, pacjentami, wizytami i rozliczeniami dla wielu klinik w ramach jednej instancji aplikacji.

## 📋 Funkcjonalności

- **Architektura Multi-tenant** - zarządzanie wieloma klinikami z pełną izolacją danych
- **Lokalizacje i gabinety** - obsługa wielu lokalizacji dla jednej kliniki
- **Zarządzanie użytkownikami** - role i uprawnienia, specjalizacje, harmonogramy pracy
- **Zarządzanie umowami i rozliczeniami** - różne typy umów, stawki rozliczeniowe
- **System dokumentów i formularzy** - przechowywanie i zarządzanie dokumentami pracowników
- **System oceny pracowników** - konfigurowalne kryteria oceny
- **Zarządzanie pacjentami** - pełna karta pacjenta, historia leczenia
- **Planowanie wizyt** - zaawansowany kalendarz, przypomnienia
- **Plany leczenia** - etapy realizacji, wyceny
- **Rozliczenia i płatności** - faktury, paragony, różne formy płatności
- **Bezpieczeństwo i audyt** - logowanie wszystkich zmian, kontrola dostępu

## 🚀 Technologie

### Backend
- Node.js
- NestJS (TypeScript)
- TypeORM
- PostgreSQL
- Redis
- JWT dla uwierzytelniania
- Swagger dla dokumentacji API

### Frontend
- React
- TypeScript
- Material-UI
- Redux Toolkit
- React Query
- React Router
- Axios

## 🛠️ Instalacja

### Wymagania wstępne
- Node.js (v16 lub nowszy)
- npm lub yarn
- PostgreSQL
- Redis
- Docker i Docker Compose (opcjonalnie)

### Klonowanie repozytorium
```bash
git clone https://github.com/your-username/dental-clinic-system.git
cd dental-clinic-system
```

### Konfiguracja zmiennych środowiskowych
```bash
# Backend
cd backend
cp .env.example .env
# Edytuj plik .env dodając odpowiednie dane

# Frontend
cd ../frontend
cp .env.example .env
# Edytuj plik .env dodając odpowiednie dane
```

### Instalacja zależności
```bash
# Backend
cd backend
npm install

# Frontend
cd ../frontend
npm install
```

### Uruchomienie bazy danych (z użyciem Docker)
```bash
docker-compose up -d postgres redis
```

### Migracje bazy danych
```bash
cd backend
npm run migration:run
```

### Uruchomienie aplikacji w trybie deweloperskim
```bash
# Backend
cd backend
npm run start:dev

# Frontend
cd ../frontend
npm run start
```

### Uruchomienie z użyciem Docker Compose
```bash
docker-compose up -d
```

## 📚 Dokumentacja

Pełna dokumentacja dostępna w katalogu `/docs`:
- [Architektura systemu](/docs/architecture/README.md)
- [Dokumentacja API](/docs/api/README.md)
- [Schematy bazy danych](/docs/database/README.md)
- [Przewodniki użytkownika](/docs/guides/README.md)

## 🧪 Testy

```bash
# Backend - testy jednostkowe
cd backend
npm run test

# Backend - testy e2e
npm run test:e2e

# Frontend
cd ../frontend
npm run test
```

## 🔄 CI/CD

Projekt wykorzystuje GitHub Actions do automatycznego:
- Uruchamiania testów
- Lintowania kodu
- Budowania i publikowania obrazów Docker
- Wdrażania w środowiskach staging i produkcyjnym

## 📝 Kontrybucja

Zachęcamy do wnoszenia wkładu w projekt! Zapoznaj się z [Przewodnikiem dla kontrybutorów](CONTRIBUTING.md), aby dowiedzieć się więcej o procesie tworzenia pull requestów.

## 📜 Licencja

Ten projekt jest licencjonowany na warunkach licencji MIT - szczegóły w pliku [LICENSE](LICENSE).

## 📞 Kontakt

W przypadku pytań lub problemów, otwórz issue lub skontaktuj się z zespołem za pośrednictwem email@example.com.
