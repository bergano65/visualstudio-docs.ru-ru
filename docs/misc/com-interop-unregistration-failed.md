---
title: "COM Interop unregistration failed | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.cannot_unregister_com2"
ms.assetid: 1172b560-c4b0-4aff-9f74-cf9b29ff76d9
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# COM Interop unregistration failed
Проблема возникла при попытке отмены регистрации старой копии сборки.  
  
 Если свойство **Регистрация для COM\-взаимодействия** установлено, система работы с проектами перед регистрацией построенного COM\-объекта попытается отменить регистрацию его старой копии.  Эти действия осуществляются для того, чтобы реестр всегда находился в актуальном состоянии.  
  
 Для доступа к свойству **Регистрация для COM\-взаимодействия** см. страницу свойств **Построение** в папке "Свойства конфигурации".  
  
 Ниже перечислены возможные причины ошибки.  
  
-   Не удается отменить регистрацию предыдущей библиотеки типов для сборки.  Возможно, в реестре есть проблемы с правами доступа.  
  
-   Не удается отменить регистрацию старой сборки.  Возможно, в реестре есть проблемы с правами доступа.  
  
 Если процесс отмены регистрации завершается с ошибкой, то возможна утечка идентификаторов GUID как для объектов, создаваемых посредством функции CoCreateInstance, так и для любой библиотеки типов.  Тем не менее, процесс построения будет успешно завершен.  
  
## См. также  
 [COM\-взаимодействие в приложениях .NET Framework](/dotnet/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications)