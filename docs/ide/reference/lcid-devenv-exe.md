---
title: -LCID (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- language default
- locale IDs, setting for IDE
- Devenv, /LCID switch
- locale IDs
- /l Devenv switch
- LCID devenv switch
- /lcid Devenv switch
ms.assetid: 3a3f4e70-ea66-4351-9d62-acb1dec30e8e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f5c3f8633721a4568b81fab31d8fe91a4c33be2f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53852077"
---
# <a name="lcid-devenvexe"></a>/LCID (devenv.exe)
Задает язык по умолчанию, используемый для текста, валюты и других значений в интегрированной среде разработки (IDE).

## <a name="syntax"></a>Синтаксис

```cmd
devenv {/LCID|/l} LocaleID
```

## <a name="arguments"></a>Аргументы
 `LocaleID` Обязательный. Код языка (LCID) для заданного вами языка.

## <a name="remarks"></a>Примечания
 Загружает интегрированную среду разработки и устанавливает естественный язык по умолчанию для среды. Это изменение сохраняется между сеансами и отражается в области **Язык интерфейса** параметров **Среда** диалогового окна **Параметры** в интегрированной среде разработки.

 Если указанный язык недоступен в системе пользователя, параметр /LCID игнорируется.

 В приведенной ниже таблице перечислены коды языка, поддерживаемые [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

|Язык|LCID|
|--------------|----------|
|Китайский (упрощенное письмо)|2052|
|Китайский (традиционное письмо)|1028|
|Английский|1033|
|Французский|1036|
|Немецкий|1031|
|Итальянский|1040|
|Японский|1041|
|Корейский|1042|
|Испанский|3082|

## <a name="example"></a>Пример
 Этот пример загружает интегрированную среду разработки с английскими строками ресурсов.

```cmd
devenv /LCID 1033
```

## <a name="see-also"></a>См. также раздел

- [Параметры командной строки для devenv](../../ide/reference/devenv-command-line-switches.md)
- [Страница "Язык интерфейса", папка "Среда", диалоговое окно "Параметры"](../../ide/reference/international-settings-environment-options-dialog-box.md)
- [Настройка макетов окон](../../ide/customizing-window-layouts-in-visual-studio.md)