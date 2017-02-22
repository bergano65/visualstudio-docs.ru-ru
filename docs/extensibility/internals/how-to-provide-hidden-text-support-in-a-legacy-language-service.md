---
title: "Практическое руководство: обеспечивает поддержку скрытого текста в языковую службу для прежних версий | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Скрытый текст, поддержка"
  - "редакторы [Visual Studio SDK] скрытые текста"
  - "языковые службы, реализация областей скрытого текста"
ms.assetid: 1c1dce9f-bbe2-4fc3-a736-5f78a237f4cc
caps.latest.revision: 21
caps.handback.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
---
# Практическое руководство: обеспечивает поддержку скрытого текста в языковую службу для прежних версий
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Можно создать области скрытого текста в дополнение к структурным областям.  Область слой текста можно клиент\-контролировать или редактор\-контролировать и используются, чтобы скрыть область текста.  Редактор отображает область скрытая как горизонтальные линии.  Примером этого представление сценария только в редакторе HTML.  
  
## Процедура  
  
#### Реализовать область скрытого текста  
  
1.  Вызов `QueryService` для  <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>.  
  
     Возвращает указатель на <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.  
  
2.  Вызов <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, передавая в указатель для данного текстового буфера.  Определяет, существует ли сеанс скрытого текста уже буфера.  
  
3.  Если таковой уже существует, то не нужно создать и указатель к существующим <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> объект возвращается.  Используйте этот указатель для просмотра и создания области скрытого текста.  В противном случае вызов <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> создание сеанса скрытого текста для буфера.  
  
     Указатель на <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> объект возвращается.  
  
    > [!NOTE]
    >  При вызове `CreateHiddenTextSession`можно указать клиента скрытого текста \(т е  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient>\).  Клиент скрытого текста, уведомляющее о если скрытый текст или структура развернуты или свернуты пользователем.  
  
4.  Вызов <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> добавление одного или более новых структурные области, указав следующие сведения в  `reHidReg` \(<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>параметр\).  
  
    1.  Укажите значение `hrtConcealed` в  `iType` элемент  <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> структура, чтобы указать, что создании скрытая область, а не структурная область.  
  
        > [!NOTE]
        >  Скрывано области скрыты, выделительнаяа строка, редактор автоматически вокруг скрытых областей, чтобы отобразить их наличие.  
  
    2.  Укажите, является ли область или редактор\-проконтролирована в клиент\-проконтролирована `dwBehavior` члены  <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> структура.  Ваша реализация структуры интеллектуального может содержать смесь областей редактора и клиент\-контролируемых структуры и скрытого текста.