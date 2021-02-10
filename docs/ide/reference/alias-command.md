---
title: Команда Alias
description: Сведения о том, как использовать команду alias для создания псевдонима для полной команды, полной команды с аргументами или для другого псевдонима.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7a20a14cc0f48e86840b770aca934b188bf152dd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969793"
---
# <a name="alias-command"></a>Команда Alias
Создает псевдоним для полной команды, полной команды с аргументами или для другого псевдонима.

> [!TIP]
> Если ввести `>alias` без аргументов, отображается текущий список псевдонимов и их определений.

## <a name="syntax"></a>Синтаксис

```cmd
Tools.Alias [/delete] [/reset] [aliasname] [aliasstring]
```

## <a name="arguments"></a>Аргументы
`aliasname`\
Необязательный элемент. Имя нового псевдонима. Если значение для `aliasname` не указано, отображается список текущих псевдонимов и их определений.

`aliasstring`\
Необязательный элемент. Полное имя команды или существующий псевдоним и любые параметры, которые вы хотите создать в виде псевдонима. Если значение для `aliasstring` не указано, отображается имя и строка для заданного псевдонима.

## <a name="switches"></a>Коммутаторы
/delete, /del или /d\
Необязательный элемент. Удаляет указанный псевдоним, убирая его из функции автозавершения.

/reset\
Необязательный элемент. Сбрасывает список предопределенных псевдонимов в исходные значения. То есть восстанавливает все предварительно определенные псевдонимы и удаляет все псевдонимы, определенные пользователем.

## <a name="remarks"></a>Комментарии
Так как псевдонимы представляют команды, они должны располагаться в начале командной строки.

При вводе данной команды нужно указать параметры сразу после нее, а не после псевдонимов. В противном случае параметр включается в состав строки псевдонима.

Параметр `/reset` запрашивает подтверждение перед восстановлением псевдонимов. У `/reset` нет краткой формы.

## <a name="examples"></a>Примеры
Этот пример создает псевдоним `upper` для полной команды Edit.MakeUpperCase.

```cmd
>Tools.Alias upper Edit.MakeUpperCase
```

Этот пример удаляет псевдоним `upper`.

```cmd
>Tools.alias /delete upper
```

Этот пример отображает список всех текущих псевдонимов и их определений.

```cmd
>Tools.Alias
```

## <a name="see-also"></a>См. также раздел

- [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Командное окно](../../ide/reference/command-window.md)
- [Поле "Поиск/команда"](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
