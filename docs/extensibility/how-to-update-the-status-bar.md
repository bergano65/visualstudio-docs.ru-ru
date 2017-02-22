---
title: "Практическое руководство: обновление строки состояния | Microsoft Docs"
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
  - "редакторы [Visual Studio SDK] прежних версий - обновление строки состояния"
ms.assetid: 7500c8a7-4913-4818-a88b-bfd1b9887cb6
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Практическое руководство: обновление строки состояния
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**строка состояния** панель элементов управления, расположенная в нижней части многие окна приложения, содержащее один или несколько линий или индикаторы текст состояния.  
  
### Обновления строки состояния  
  
1.  Реализация <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> в каждом отдельном объекте представления \(DocView\), редактор, например представление формы и представление кода.  
  
2.  При вызове интегрированной среды разработки <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>обновите сведения  **строка состояния** путем вызова методов  <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>.  
  
    > [!NOTE]
    >  Вызовы интегрированной среды разработки <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> окно документа только если для исходной активированы.  Для получения остатка времени, что окно документа активно, необходимо обновить **строка состояния** подробные сведения о том, как изменяется состояние пользовательского редактора.  
  
## Отказоустойчивость  
 A **строка состояния** содержит 4 отдельных полей:  
  
-   Текст состояния  
  
-   Индикатор выполнения  
  
-   Анимированный значок  
  
-   Данные редактора  
  
 Дополнительные сведения см. в разделе [Строки состояния](/visual-cpp/mfc/status-bars).  
  
 Интегрированная среда разработки автоматически вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> метод вашего  <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> реализация активировано при обработке окно документа.  
  
 Разработчик VSPackage отвечает за обновление текста состояния в строке состояния.  Интегрированная среда разработки сбросит эта строка "ПОДГОТАВЛИВАЕТ", если текстовое поле состояния набор для очистки текст \(""\) во время простоя.  
  
## См. также  
 [Строки состояния](/visual-cpp/mfc/status-bars)