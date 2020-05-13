---
title: -LCID (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- language default
- locale IDs, setting for IDE
- Devenv, /L switch
- Devenv, /LCID switch
- locale IDs
- L Devenv switch
- /L Devenv switch
- LCID devenv switch
- /LCID Devenv switch
ms.assetid: 3a3f4e70-ea66-4351-9d62-acb1dec30e8e
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cabbf36adb5019543b3cfb72b0b0e56976517d2d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/18/2020
ms.locfileid: "77557932"
---
# <a name="lcid-devenvexe"></a>/LCID (devenv.exe)

Задает язык по умолчанию, используемый для текста, валюты и других значений в интегрированной среде разработки.

## <a name="syntax"></a>Синтаксис

```shell
devenv {/LCID|/L} LocaleID
```

## <a name="arguments"></a>Аргументы

- *LocaleID*

  Обязательный элемент. Код языка (LCID) для заданного вами языка.

## <a name="remarks"></a>Remarks

Загружает интегрированную среду разработки и устанавливает естественный язык по умолчанию для среды. Это изменение сохраняется между сеансами. Интегрированная среда разработки показывает его в поле **Инструменты** > **Параметры** > **Среда** > **Международные параметры** > **Язык**.

Если указанный язык недоступен в системе, параметр `/LCID` игнорируется.

В приведенной ниже таблице перечислены коды языка, поддерживаемые Visual Studio.

|Язык|LCID|
|--------------|----------|
|Китайский (упрощенное письмо)|2052|
|Китайский (традиционное письмо)|1028|
|Чешский|1029|
|Английский|1033|
|Французский|1036|
|Немецкий|1031|
|Итальянский|1040|
|Японский|1041|
|Корейский|1042|
|Польский|1045|
|Португальский (Бразилия)|1046|
|Русский|1049|
|Испанский|3082|
|Турецкий|1055

## <a name="example"></a>Пример

Этот пример загружает интегрированную среду разработки с английскими строками ресурсов.

```shell
devenv /LCID 1033
```

## <a name="see-also"></a>См. также раздел

- [Параметры командной строки для devenv](../../ide/reference/devenv-command-line-switches.md)
- [Страница "Язык интерфейса", папка "Среда", диалоговое окно "Параметры"](../../ide/reference/international-settings-environment-options-dialog-box.md)
- [Настройка макетов окон](../../ide/customizing-window-layouts-in-visual-studio.md)
