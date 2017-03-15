---
title: "Возможности IntelliSense в Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IntelliSense [Visual Basic]"
  - "IntelliSense [Visual Studio], Visual Basic"
ms.assetid: 4dec8753-05e5-4f74-b304-5f8c4ed8723b
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# Возможности IntelliSense в Visual Basic
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Редактор исходного кода в Visual Basic предоставляет следующие функции IntelliSense:  
  
-   Синтаксические подсказки  
  
     Синтаксические подсказки отображают синтаксис вводимого оператора.  Это может пригодиться для таких операторов, как [Declare](/dotnet/visual-basic/language-reference/statements/declare-statement).  
  
## Автоматическое заполнение  
  
-   Заполнение по различным зарезервированным словам  
  
     Например, если набрать `goto` и поставить пробел, IntelliSense в выпадающем меню отображает список определенных меток.  Среди других поддерживаемых ключевых слов такие как `Exit`, `Implements`, `Option` и `Declare`.  
  
-   Заполнение `Enum` и `Boolean`  
  
     Если оператор ссылается на член перечисления, IntelliSense отображает список членов `Enum`.  Если оператор ссылается на `Boolean`, IntelliSense отображает выпадающее меню true\-false.  
  
 Заполнение может быть по умолчанию отключено путем отмены выбора **Отображать автоматически список членов** на странице свойств **Общие** в папке **Visual Basic**.  
  
 Заполнение может вызываться вручную посредством вызова параметра Список членов, Завершить слово или нажатием сочетания клавиш ALT\+СТРЕЛКА ВПРАВО.  Дополнительные сведения см. в разделе [Использование технологии IntelliSense](../ide/using-intellisense.md).  
  
## IntelliSense in Zone  
 IntelliSense in Zone помогает разработчикам на Visual Basic, которым приходится разворачивать приложения через [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] и которые ограничены параметрами частичного доверия.  Возможности:  
  
-   Возможность выбора разрешений для приложения.  
  
-   Отображение API в выбранной зоне как доступных в списке членов, а также API, для которых требуются дополнительные, как недоступных.  
  
 Дополнительные сведения см. в разделе [Управление доступом для кода для приложения ClickOnce](../deployment/code-access-security-for-clickonce-applications.md).  
  
## См. также  
 [Использование технологии IntelliSense](../ide/using-intellisense.md)