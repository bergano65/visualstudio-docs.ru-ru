---
title: "Создание подключаемого модуля системы управления версиями | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "подключаемые модули, системы управления версиями"
  - "подключаемые модули управления версиями"
  - "Система управления версиями [Visual Studio SDK] подключаемых модулей"
ms.assetid: c7e69fa4-150e-469a-a6fc-fa1260bdbb07
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# Создание подключаемого модуля системы управления версиями
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Пакет SDK для Visual Studio предоставляет ресурсы, которые позволяют добавлять возможности системы управления версиями к [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированная среда разработки \(ide\).  Он позволяет использовать любое подключаемый модуль DLL, которое соответствует с API системы управления версиями конспектированное подключаемого модуля в этой документации.  
  
## В этом подразделе  
 [Начало работы](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)  
 Описывает, как устанавливать подключаемый модуль системы управления версиями и выбирает версии API в данный момент доступной подключаемых модулей системы управления версиями.  
  
 [Архитектура](../../extensibility/internals/source-control-plug-in-architecture.md)  
 Используется схема архитектуры для объяснения интеграцию подключаемого модуля для системы управления версиями [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированная среда разработки.  
  
 [Руководство по проведению тестирования для подключаемых модулей системы управления версиями](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)  
 Предоставляет сведения о том, как проверить установку и операция подключаемых модулей системы управления версиями.  
  
## Связанные подразделы  
 [Создание VSPackage управления источника](../../extensibility/internals/creating-a-source-control-vspackage.md)  
 Обсуждается создание система управления версиями VSPackage, которая не только предоставляют функциональные возможности системы управления версиями, но заменить [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] пользовательский интерфейс системы управления версиями.  
  
 [Подключаемые модули управления версиями](../../extensibility/source-control-plug-ins.md)  
 Предоставляет полный листинг всех элементов в api\-интерфейсе подключаемых модулей системы управления версиями.  
  
 [Система управления версиями](../../extensibility/internals/source-control.md)  
 Описывает параметры для реализации системы управления версиями, как интегрированная функция [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].