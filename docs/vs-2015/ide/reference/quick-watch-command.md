---
title: Команда Quick Watch | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.quickwatch
helpviewer_keywords:
- Quick Watch command
- Debug.Quickwatch command
ms.assetid: 9670ac3a-8f2f-4874-974d-cb87d3b0cde1
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: da9ba9572e121a9eba74cd8d624789032f1bb4a1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665659"
---
# <a name="quick-watch-command"></a>Команда Quick Watch
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Отображает выбранный или указанный текст в поле "Выражение" [диалогового окна "Быстрая проверка"](https://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867). Это диалоговое окно предназначено для вычисления текущего значения переменной или выражения, распознанного отладчиком, либо содержимого регистра. Кроме того, можно изменить значение любой неконстантной переменной или содержимое регистров.

## <a name="syntax"></a>Синтаксис

```
Debug.QuickWatchq [text]
```

## <a name="arguments"></a>Аргументы
 `text` Необязательный. Текст для добавления в диалоговое окно **Быстрая проверка**

## <a name="remarks"></a>Remarks
 Если параметр `text` опущен, выделенный текст или слово в позиции курсора добавляется в окно контрольных значений.

## <a name="example"></a>Пример

```
>Debug.QuickWatch
```

## <a name="see-also"></a>См. также:
 [Как использовать диалоговое окно "Быстрая проверка](https://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867) " команды [Visual Studio командное](../../ide/reference/visual-studio-commands.md) [окно](../../ide/reference/command-window.md) [Поиск/команда](../../ide/find-command-box.md) [Visual Studio псевдонимы команд](../../ide/reference/visual-studio-command-aliases.md)
