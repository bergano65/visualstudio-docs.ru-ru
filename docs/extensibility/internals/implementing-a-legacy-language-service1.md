---
title: "Реализация Service1 языка прежних версий | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Управление службами языка"
ms.assetid: df638f24-166d-4b80-be82-c9c39ca7a556
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# Реализация службы языка прежних версий
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Можно использовать классы в платформа управляемых пакетов \(MPF\) для реализации прежних версий языковую службу, поддерживает широкий набор функций, например подсветку синтаксиса, парные фигурные скобки и завершения IntelliSense.  
  
 Устаревший языковые службы реализуются как частью VSPackage, но это использование расширений MEF новый способ реализации возможностей службы языка. Чтобы больше узнать о новый способ реализации службы языка, в разделе [Редактор и расширения службы языка](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
>  Мы рекомендуем начать использовать новый редактор API как можно быстрее. Это улучшает производительность службы языка и позволяют воспользоваться преимуществами новых функций редактора.  
  
## В этом подразделе  
 [Общие сведения о службе устаревших языка](../../extensibility/internals/legacy-language-service-overview.md)  
 Обзор возможностей службы языка, поддерживаемые в MPF.  
  
 [Реализация службы языка](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
 Описывает, что требуется реализовать языковую службу с помощью MPF.  
  
 [Регистрация службы языка](../../extensibility/internals/registering-a-legacy-language-service1.md)  
 Описание действий, которые необходимо зарегистрировать службу язык на основе MPF с [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Средство синтаксического анализа языка прежних версий службы и сканера](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)  
 Описывает два средства синтаксического анализа, которые необходимы для реализации всех возможностей службы языка с помощью MPF.  
  
 [Пошаговое руководство: Создание языковую службу для прежних версий](../../extensibility/internals/walkthrough-creating-a-legacy-language-service.md)  
 Предоставляет основные шаги, необходимые для реализации службы MPF языка в VSPackage.  
  
 [Пошаговое руководство: Получение списка установленных текстов \(реализация прежних версий\)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)  
 Демонстрирует методики получение списка установленных текстов.  
  
 [Компоненты прежних версий языка службы](../../extensibility/internals/legacy-language-service-features1.md)  
 Ссылки на разделы с подробным описанием, что нужно сделать, чтобы реализовать все возможности языковую службу с помощью MPF.