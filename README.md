# Privátní Cloud s autorským rozhraním

> Dokumentace k školnímu projektu | Platform: ownCloud | Server: Debian Linux | Rok: 2026

---

## 1. Anotace

Tato práce se zabývá instalací, konfigurací a vizuální modifikací privátního cloudového úložiště založeného na platformě **ownCloud**. Cílem projektu bylo vytvořit bezpečné prostředí pro správu dat, které kombinuje stabilitu open-source řešení s moderním, minimalistickým designem.

---

## 2. Úvod

V dnešní době, kdy je soukromí dat neustále skloňovaným tématem, roste poptávka po řešeních, která uživatelům umožňují mít plnou kontrolu nad jejich digitálním obsahem. Veřejné cloudové služby jako Dropbox nebo Google Drive sice nabízejí pohodlí, ale za cenu ztráty absolutní kontroly nad fyzickým umístěním dat a soukromím.

Projekt se zaměřuje na nasazení vlastní instance systému ownCloud na linuxovém serveru. Hlavním přínosem práce není pouze samotné zprovoznění služby, ale její hloubková modifikace na úrovni CSS šablon — cílem bylo vytvořit rozhraní, které je estetické, intuitivní a profesionální. Projekt řeší technické výzvy spojené s konfigurací webového serveru Nginx, laděním PHP procesů a přepisováním hluboko vnořených stylů (CSS overrides).

---

## 3. Ekonomická rozvaha

**Konkurence:** Hlavními konkurenty jsou komerční služby (Google Drive, Microsoft OneDrive).

**Výhody projektu:**

- 💰 **Nulové měsíční poplatky** — platí se pouze za hardware a energii, nikoliv za cloudový prostor.
- 🔒 **Soukromí** — data neprocházejí skrze servery třetích stran.
- 🎨 **Customizace** — vzhled přizpůsoben pomocí vlastního CSS (odstranění log, změna barev a layoutu).
- 📡 **Propagace** — projekt je určen pro interní potřeby nebo malé týmy; integrace do firemního rozcestníku.

**Návratnost investice (ROI):** Při srovnání s cenou 2 TB plánu u komerčních cloudů je návratnost investice do vlastního serveru přibližně **12–18 měsíců**.

---

## 4. Vývoj

### Použité technologie

| Vrstva | Technologie |
|---|---|
| Server | Linux (Debian) |
| Webový server | Nginx (reverzní proxy, SSL) |
| Databáze | MariaDB |
| Backend | PHP 7.4 |
| Frontend | HTML5, CSS3 (Custom Theme Overrides) |

### Architektura tématu

Systém je rozdělen na jádro (Core), aplikace (Apps) a složku témat (Themes). Veškeré úpravy probíhaly ve složce `/themes/cyber`, což zajišťuje integritu při aktualizacích.

### Průběh vývoje

Vývoj probíhal iterativně. Nejprve byla zprovozněna stabilní serverová část (LEMP stack). Následně byly analyzovány CSS třídy původního rozhraní a pomocí nástrojů pro vývojáře v prohlížeči byly definovány nové styly. Velkou výzvou bylo fixování absolutně pozicovaných prvků v seznamu souborů.

---

## 5. Testování

| ID | Scénář | Očekávaný výsledek | Výsledek |
|---|---|---|---|
| T01 | Nasazení (Deploy) | Spuštění instalace a připojení k databázi | ✅ Úspěch |
| T02 | Přihlášení uživatele | Ověření jména/hesla, přesměrování do dashboardu | ✅ Úspěch |
| T03 | Nahrání souboru | Upload 100MB souboru přes drag-and-drop | ✅ Úspěch |
| T04 | Aplikace vzhledu | Načtení custom CSS bez chyb (HTTP 200) | ✅ Úspěch |
| T05 | Responsivita | Přístup z mobilního zařízení, správné zobrazení menu | ✅ Úspěch |

---

## 6. Uživatelská příručka (Nasazení)

**Požadavky:** Server s Debian Linuxem, nainstalovaný Nginx a PHP-FPM 7.4.

**Kroky:**

1. **Instalace** — stáhnout archiv ownCloud do `/var/www/html`.
2. **Aktivace tématu** — složku s CSS kódem vložit do `/themes/`. V `config.php` přidat:
   ```php
   'theme' => 'nazev_tematu',
   ```
3. **Spuštění** — přistoupit na IP adresu serveru přes prohlížeč a dokončit průvodce nastavením.

---

## 7. Licence

| Komponenta | Licence |
|---|---|
| ownCloud core | GNU AGPLv3 |
| Vlastní CSS styly | MIT |

---

## 8. Odkazy

- 🔗 **Repozitář:** [github.com/San2497/Muj-Cloude](https://github.com/San2497/Muj-Cloude)
- 🌐 **Demo:** [nguyen7-wa.dev.spsejecna.net/owncloud](http://nguyen7-wa.dev.spsejecna.net/owncloud)

---

## 9. Závěr

V rámci projektu se podařilo úspěšně implementovat privátní cloudové úložiště, které plně nahrazuje komerční alternativy. Během práce byly prohloubeny znalosti v oblasti správy Linuxových serverů a pokročilého CSS designu. Výsledek splňuje všechny požadavky na bezpečnost, stabilitu i estetickou úroveň rozhraní.
