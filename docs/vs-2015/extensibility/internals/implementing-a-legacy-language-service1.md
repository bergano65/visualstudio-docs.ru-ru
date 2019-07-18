---
title: Реализация языковой службы прежних версий1 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, managed
ms.assetid: df638f24-166d-4b80-be82-c9c39ca7a556
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 20493991d8e0740ca045f041e2ba94cf3735ad1a
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436112"
---
# <a name="implementing-a-legacy-language-service"></a>Реализация языковой службы прежних версий
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Классы в managed package framework (MPF) можно использовать для реализации прежних версий языковой службы, которая поддерживает широкий спектр функций, например выделение синтаксиса, парные фигурные скобки и завершение IntelliSense.  
  
 Устаревший языковой службы реализуются как часть пакета VSPackage, но новый способ реализовать функции языковой службы является использование расширений MEF. Чтобы подробнее узнать о новых способах реализации языковой службы, см. в разделе [редактора и языковой службы расширения](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
> Мы рекомендуем начать использовать новый редактор API как можно скорее. Это улучшит производительность службы языка и позволяют воспользоваться преимуществами новых функций редактора.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Обзор языковой службы прежних версий](../../extensibility/internals/legacy-language-service-overview.md)  
 Обзор возможностей службы языка, которые поддерживаются в MPF.  
  
 [Реализация языковой службы прежних версий](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
 Описывает, что он должен реализовывать языковую службу с помощью MPF.  
  
 [Регистрация языковой службы прежних версий](../../extensibility/internals/registering-a-legacy-language-service1.md)  
 Описание действий, которые необходимо зарегистрировать службу языка на основе MPF с [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 [Средство синтаксического анализа и сканер языковой службы прежних версий](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)  
 Описывает два средства синтаксического анализа, которые необходимы для реализации всех возможностей службы языка с помощью MPF.  
  
 [Пошаговое руководство: создание языковой службы прежних версий](../../extensibility/internals/walkthrough-creating-a-legacy-language-service.md)  
 Предоставляет основные шаги, необходимые для реализации службы языка MPF в VSPackage.  
  
 [Пошаговое руководство: получение списка установленных фрагментов кода (реализация прежних версий)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)  
 Демонстрирует методы получения списка фрагментов кода.  
  
 [Функции языковой службы прежних версий](../../extensibility/internals/legacy-language-service-features1.md)  
 Ссылки на разделы с подробным описанием, что необходимо сделать для реализации всех возможностей службы языка с помощью MPF.
