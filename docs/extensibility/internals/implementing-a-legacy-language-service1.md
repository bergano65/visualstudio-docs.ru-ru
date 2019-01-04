---
title: Реализация языковой службы прежних версий1 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, managed
ms.assetid: df638f24-166d-4b80-be82-c9c39ca7a556
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d3218a8cf1c61fb9b88520702a953f2288e19b3c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53855891"
---
# <a name="implementing-a-legacy-language-service"></a>Реализация языковой службы прежних версий
Классы в managed package framework (MPF) можно использовать для реализации прежних версий языковой службы, которая поддерживает широкий спектр функций, например выделение синтаксиса, парные фигурные скобки и завершение IntelliSense.  
  
 Устаревший языковой службы реализуются как часть пакета VSPackage, но новый способ реализовать функции языковой службы является использование расширений MEF. Чтобы подробнее узнать о новых способах реализации языковой службы, см. в разделе [редактора и языковой службы расширения](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
>  Мы рекомендуем начать использовать новый редактор API как можно скорее. Это улучшит производительность службы языка и позволяют воспользоваться преимуществами новых функций редактора.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Обзор языковой службы прежних версий](../../extensibility/internals/legacy-language-service-overview.md)  
 Обзор возможностей службы языка, которые поддерживаются в MPF.  
  
 [Реализация языковой службы прежних версий](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
 Описывает, что он должен реализовывать языковую службу с помощью MPF.  
  
 [Регистрация языковой службы прежних версий](../../extensibility/internals/registering-a-legacy-language-service1.md)  
 Описание действий, которые необходимо зарегистрировать службу языка на основе MPF с [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Средство синтаксического анализа и сканер языковой службы прежних версий](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)  
 Описывает два средства синтаксического анализа, которые необходимы для реализации всех возможностей службы языка с помощью MPF.  
  
 [Пошаговое руководство: Создание языковой службы прежних версий](../../extensibility/internals/walkthrough-creating-a-legacy-language-service.md)  
 Предоставляет основные шаги, необходимые для реализации службы языка MPF в VSPackage.  
  
 [Пошаговое руководство: Получение списка фрагментов кода (реализация прежних версий)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)  
 Демонстрирует методы получения списка фрагментов кода.  
  
 [Функции языковой службы прежних версий](../../extensibility/internals/legacy-language-service-features1.md)  
 Ссылки на разделы с подробным описанием, что необходимо сделать для реализации всех возможностей службы языка с помощью MPF.