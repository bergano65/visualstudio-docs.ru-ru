---
title: "Страница &quot;Язык интерфейса&quot;, папка &quot;Среда&quot;, диалоговое окно &quot;Параметры&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Environment.InternationalSettings"
  - "VS.ToolsOptionsPages.Environment.International_Settings"
  - "VS.Environment.International Settings"
  - "VS.ToolsOptionsPag.Environment.International_Settings"
helpviewer_keywords: 
  - "диалоговое окно "Международные параметры""
  - "языки, параметры среды"
  - "Диалоговое окно "Параметры", международные параметры"
  - "языки, указание значения по умолчанию"
ms.assetid: e3a8815c-6995-4099-8e88-34f91fad55b2
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# Страница &quot;Язык интерфейса&quot;, папка &quot;Среда&quot;, диалоговое окно &quot;Параметры&quot;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

На странице «Выбор языка» можно изменить язык по умолчанию, если на компьютере установлено несколько языковых версий интегрированной среды разработки \(IDE\).  Чтобы открыть это диалоговое окно, выберите **Параметры** в меню **Сервис**, а затем выберите **Выбор языка** в папке **Среда**.  Если эта страница отсутствует в списке, выберите **Показать все параметры** в диалоговом окне **Параметры**.  
  
> [!NOTE]
>  Доступные в диалоговых окнах параметры, а также названия и расположение команд меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска.  Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров**.  Дополнительные сведения см. в разделе [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ru-ru/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 **Язык**  
 Содержит список доступных языков для языковых версий установленного продукта.  Этот параметр недоступен, если на компьютере не установлено несколько языковых версий.  Если среда разработки является общей для продуктов на разных языках, язык меняется на **Тот же, что и для Microsoft Windows**.  
  
> [!CAUTION]
>  В системе с несколькими установленными языками средства построения Visual C\+\+ \(cl.exe, link.exe, nmake.exe, bscmake.exe и связанные файлы\) не зависят от этого параметра.  Эти средства используют версию для самого последнего установленного языка. Средства для ранее установленных языков перезаписываются, поскольку средства построения Visual C\+\+ не используют модель вспомогательных библиотек DLL.  
  
## См. также  
 [Установка нескольких языковых версий Visual Studio](../Topic/Installing%20Multiple%20Language%20Versions%20of%20Visual%20Studio.md)   
 [Диалоговое окно "Параметры среды"](../../ide/reference/environment-options-dialog-box.md)