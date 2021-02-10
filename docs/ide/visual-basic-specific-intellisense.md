---
title: Visual Basic IntelliSense
description: Узнайте, как использовать функции IntelliSense, предлагаемые редактором исходного кода Visual Basic.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.Basic.IntelliSense
helpviewer_keywords:
- IntelliSense [Visual Basic]
- IntelliSense [Visual Studio], Visual Basic
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1420165c8ca574c74efe6911bb9c5635e729a260
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955558"
---
# <a name="intellisense-for-visual-basic-code-files"></a>IntelliSense для файлов кода Visual Basic

Редактор исходного кода Visual Basic предоставляет следующие функции IntelliSense:

## <a name="syntax-tips"></a>Советы по синтаксису

Советы по синтаксису отображают сведения о синтаксисе вводимого вами оператора. Это удобно для таких операторов, как [Declare](/dotnet/visual-basic/language-reference/statements/declare-statement).

## <a name="automatic-completion"></a>Автоматическое завершение

- Завершение различных ключевых слов

     Например, если ввести `goto` и пробел, IntelliSense отображает список определенных меток в раскрывающемся меню. К другим поддерживаемым ключевым словам относятся `Exit`, `Implements`, `Option` и `Declare`.

- Завершение `Enum` и `Boolean`

    Если оператор ссылается на член перечисления, IntelliSense отображает список членов `Enum`. Если оператор ссылается на `Boolean`, IntelliSense отображает раскрывающееся меню с логическими значениями true и false.

Чтобы отключить завершение по умолчанию, отмените выбор элемента **Автоматически отображать список членов** на странице свойств **Общие** в папке **Visual Basic**.

Вы можете включить завершение вручную, вызвав функцию "Список членов", "Завершить слово" или нажав клавиши **ALT**+**СТРЕЛКА ВПРАВО**. Дополнительные сведения см. в статье [Использование IntelliSense](../ide/using-intellisense.md).

## <a name="intellisense-in-zone"></a>IntelliSense в заданной зоне безопасности

IntelliSense в заданной зоне безопасности помогает разработчикам на Visual Basic, которым нужно развертывать приложения с помощью [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], ограничившись при этом частичным доверием. Этот компонент:

- позволяет выбрать разрешения, с которыми будет выполняться приложение;

- отображает API в выбранной зоне как доступные в списке членов, а API, которым нужны дополнительные разрешения, как недоступные.

Дополнительные сведения см. в статье [Управление доступом для кода для приложения ClickOnce](../deployment/code-access-security-for-clickonce-applications.md).

## <a name="filtered-completion-lists"></a>Фильтрованные списки завершения

В Visual Basic списки завершения IntelliSense имеют два элемента управления "Вкладка", находящиеся в нижней части списков. Вкладка **Общие**, которая выбрана по умолчанию, содержит элементы, которые чаще всего используются для завершения вводимого оператора. Вкладка **Все** содержит все элементы, доступные для автоматического завершения, включая и те, которые указаны на вкладке **Общие**.

## <a name="see-also"></a>См. также раздел

- [Использование IntelliSense](../ide/using-intellisense.md)
