---
title: Возможности IntelliSense в Visual Basic | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense [Visual Basic]
- IntelliSense [Visual Studio], Visual Basic
ms.assetid: 4dec8753-05e5-4f74-b304-5f8c4ed8723b
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ce0d1f2fd5c4ea8549f638f97846fdf7a1726b90
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/19/2019
ms.locfileid: "54796897"
---
# <a name="visual-basic-specific-intellisense"></a>Возможности IntelliSense в Visual Basic
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Редактор исходного кода Visual Basic предоставляет следующие функции IntelliSense:  
  
-   Советы по синтаксису  
  
     Советы по синтаксису отображают сведения о синтаксисе вводимого вами оператора. Это удобно для таких операторов, как [Declare](http://msdn.microsoft.com/library/d3f21fb0-b804-4c99-97ed-583b23894cf1).  
  
## <a name="automatic-completion"></a>Автоматическое завершение  
  
- Завершение различных ключевых слов  
  
   Например, если ввести `goto` и пробел, IntelliSense отображает список определенных меток в раскрывающемся меню. К другим поддерживаемым ключевым словам относятся `Exit`, `Implements`, `Option` и `Declare`.  
  
- Завершение `Enum` и `Boolean`  
  
   Если оператор ссылается на член перечисления, IntelliSense отображает список членов `Enum`. Если оператор ссылается на `Boolean`, IntelliSense отображает раскрывающееся меню с логическими значениями true и false.  
  
  Чтобы отключить завершение по умолчанию, отмените выбор элемента **Автоматически отображать список членов** на странице свойств **Общие** в папке **Visual Basic**.  
  
  Вы можете включить завершение вручную, вызвав функцию "Список членов", "Завершить слово" или нажав клавиши ALT+СТРЕЛКА ВПРАВО. Дополнительные сведения см. в статье [Using IntelliSense](../ide/using-intellisense.md) (Использование IntelliSense).  
  
## <a name="intellisense-in-zone"></a>IntelliSense в заданной зоне безопасности  
 IntelliSense в заданной зоне безопасности помогает разработчикам на Visual Basic, которым нужно развертывать приложения с помощью [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], ограничившись при этом частичным доверием. Этот компонент:  
  
- позволяет выбрать разрешения, с которыми будет выполняться приложение;  
  
- отображает API в выбранной зоне как доступные в списке членов, а API, которым нужны дополнительные разрешения, как недоступные.  
  
  Дополнительные сведения см. в статье [Управление доступом для кода для приложения ClickOnce](../deployment/code-access-security-for-clickonce-applications.md).  
  
## <a name="see-also"></a>См. также раздел  
 [Использование технологии IntelliSense](../ide/using-intellisense.md)
