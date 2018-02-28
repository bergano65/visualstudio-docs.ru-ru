---
title: "Реализация языка прежних версий Service1 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language services, managed
ms.assetid: df638f24-166d-4b80-be82-c9c39ca7a556
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 304d99c1ddd5fdfddba0c4df88fc4eeeb9dcb7ac
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-a-legacy-language-service"></a>Реализация службы языка для прежних версий
Классы managed package framework (MPF) можно использовать для реализации прежних версий языковую службу, поддерживает широкий набор функций, например выделение синтаксиса, парные фигурные скобки и завершения IntelliSense.  
  
 Прежних версий языка службы реализованы как часть пакета VSPackage, но новой реализации возможностей службы языка можно выполнить с помощью расширений MEF. Чтобы больше узнать о новых способ реализации языковую службу, в разделе [редактора и расширения службы языка](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
>  Мы рекомендуем начать использовать новый редактор API, как можно быстрее. Это повысит быстродействие языковой службы и позволяют воспользоваться преимуществами новых функций редактора.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Обзор языковой службы прежних версий](../../extensibility/internals/legacy-language-service-overview.md)  
 Обзор возможностей службы языка, которые поддерживаются в MPF.  
  
 [Реализация службы языка для прежних версий](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
 Описывает требования для реализации языковую службу с помощью MPF.  
  
 [Регистрация службы языка для прежних версий](../../extensibility/internals/registering-a-legacy-language-service1.md)  
 Описывает шаги, необходимые для регистрации службы язык на основе MPF с [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Средство синтаксического анализа и сканер языковой службы прежних версий](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)  
 Описывает два средства синтаксического анализа, которые необходимы для реализации всех возможностей службы языка с помощью MPF.  
  
 [Пошаговое руководство. Создание языковой службы прежних версий](../../extensibility/internals/walkthrough-creating-a-legacy-language-service.md)  
 Предоставляет основные шаги, необходимые для реализации службы языка MPF в VSPackage.  
  
 [Пошаговое руководство. Получение списка фрагментов кода (реализация прежних версий)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)  
 Демонстрирует методы получения список установленных фрагменты.  
  
 [Возможности службы прежних версий языка](../../extensibility/internals/legacy-language-service-features1.md)  
 Ссылки на разделы с подробным описанием, что необходимо сделать, чтобы реализовать все возможности языковую службу с помощью MPF.