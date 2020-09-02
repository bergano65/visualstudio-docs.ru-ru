---
title: Команда "Псевдоним" | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- tools.alias
helpviewer_keywords:
- aliases, Visual Studio commands
- commands, aliases
- Tools.Alias command
- command aliases
- alias command
ms.assetid: bdf857df-b5d5-450f-8c10-a6fd4dccc130
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6da744b0db9e41cd1e5039a1bd0d5c93bc4c734a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651692"
---
# <a name="alias-command"></a>Команда Alias
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Создает псевдоним для полной команды, полной команды с аргументами или для другого псевдонима.

> [!TIP]
> Если ввести `>alias` без аргументов, отображается текущий список псевдонимов и их определений.

## <a name="syntax"></a>Синтаксис

```
Tools.Alias [/delete] [/reset] [aliasname] [aliasstring]
```

## <a name="arguments"></a>Аргументы
 `aliasname` Необязательный. Имя нового псевдонима. Если значение для `aliasname` не указано, отображается список текущих псевдонимов и их определений.

 `aliasstring` Необязательный. Полное имя команды или существующий псевдоним и любые параметры, которые вы хотите создать в виде псевдонима. Если значение для `aliasstring` не указано, отображается имя и строка для заданного псевдонима.

## <a name="switches"></a>Коммутаторы
 /delete, /del или /d Необязательный. Удаляет указанный псевдоним, убирая его из функции автозавершения.

 /reset Необязательный. Сбрасывает список предопределенных псевдонимов в исходные значения. То есть восстанавливает все предварительно определенные псевдонимы и удаляет все псевдонимы, определенные пользователем.

## <a name="remarks"></a>Remarks
 Так как псевдонимы представляют команды, они должны располагаться в начале командной строки.

 При вводе данной команды нужно указать параметры сразу после нее, а не после псевдонимов. В противном случае параметр включается в состав строки псевдонима.

 Параметр `/reset` запрашивает подтверждение перед восстановлением псевдонимов. У `/reset` нет краткой формы.

## <a name="examples"></a>Примеры
 Этот пример создает псевдоним `upper` для полной команды Edit.MakeUpperCase.

```
>Tools.Alias upper Edit.MakeUpperCase
```

 Этот пример удаляет псевдоним `upper`.

```
>Tools.alias /delete upper
```

 Этот пример отображает список всех текущих псевдонимов и их определений.

```
>Tools.Alias
```

## <a name="see-also"></a>См. также:
 Команды [Visual Studio командное](../../ide/reference/visual-studio-commands.md) [окно](../../ide/reference/command-window.md) [Найти/Команда](../../ide/find-command-box.md) командные [псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
