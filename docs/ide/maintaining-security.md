---
title: Обеспечение безопасности приложений в Visual Studio | Документы Майкрософт
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- unauthorized access
- Baseline Security Analyzer
- Microsoft Baseline Security Analyzer
- security [.NET Framework], best practices
- MBSA (Microsoft Baseline Security Analyzer)
- security [.NET Framework], maintaining after deployment
ms.assetid: 621d10c1-842b-4902-be60-bb9719591751
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6fb75bfe3c9e479e67c766137ee84e919f9a6710
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="maintaining-security"></a>Обеспечение безопасности

Часто считается, что ценой безопасности является постоянная бдительность. Даже если на этапе разработки приложения все проблемы безопасности были решены, следует предполагать наличие слабых мест в системе безопасности после развертывания. Аудит приложения и анализ журналов событий позволяет обнаружить некоторые недостатки, которые ранее не были видны.

Кроме того, необходимо не только следить за безопасностью отдельного приложения, но и знать обо всех текущих угрозах и слабых местах системы безопасности платформы, на которой работает приложение, и других продуктов, от которых зависит работа приложения.

[Безопасность, конфиденциальность и учетные записи](https://support.microsoft.com/products/microsoft-account?category=privacy#security-privacy-accounts-help=windows-8&v0h=winrttab1&v1h=win8tab1&v2h=win7tab1&v3h=winvistatab1)&mdash;Помощь по вопросам безопасности, конфиденциальности и учетных записей пользователей, включая сведения о вирусах, паролях, родительском контроле, брандмауэрах и шифровании диска.

[Бюллетени по обновлениям для системы безопасности Майкрософт](https://technet.microsoft.com/security/bulletins.aspx)&mdash;На этой странице можно легко найти предыдущие выпуски бюллетеней. Информационные бюллетени предназначены для специалистов в области информационных технологий и содержат подробные сведения о последних обновлениях системы безопасности.

[Microsoft Baseline Security Analyzer](https://www.microsoft.com/download/details.aspx?id=7558)&mdash;Microsoft Baseline Security Analyzer (MBSA) — это средство, которое может использоваться домашними или корпоративными пользователями, а также администраторами для проверки одного или нескольких компьютеров с ОС Windows на наличие типичных ошибок настройки системы безопасности.