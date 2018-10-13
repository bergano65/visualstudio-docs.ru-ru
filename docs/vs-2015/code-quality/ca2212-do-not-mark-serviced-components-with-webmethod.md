---
title: 'CA2212: Не следует помечать обслуживаемые компоненты атрибутом WebMethod | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
helpviewer_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
ms.assetid: 774bc55d-e588-48ee-8f38-c228580feca2
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: bd9ebcf576e3a7be1f573604b6be6a9d8eb6d4fc
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49273667"
---
# <a name="ca2212-do-not-mark-serviced-components-with-webmethod"></a>CA2212: не следует помечать обслуживаемые компоненты атрибутом WebMethod
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|DoNotMarkServicedComponentsWithWebMethod|
|CheckId|CA2212|
|Категория|Microsoft.Usage|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Метод в тип, наследующий от <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> помечается <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>.

## <a name="rule-description"></a>Описание правила
 <xref:System.Web.Services.WebMethodAttribute> применяется к методам XML-веб-службы, которые были созданы с помощью ASP.NET; Она позволяет вызывать метод из удаленных веб-клиентов. Метод и класс должен быть открытыми и выполняться в веб-приложения ASP.NET. <xref:System.EnterpriseServices.ServicedComponent> типы, которые размещаются приложения COM + и могут использовать службы COM +. <xref:System.Web.Services.WebMethodAttribute> не применяется к <xref:System.EnterpriseServices.ServicedComponent> типов, так как они не предназначены для сценариев. В частности, добавление атрибута к <xref:System.EnterpriseServices.ServicedComponent> метод не выполняет метод вызываемый из удаленных веб-клиентов. Так как <xref:System.Web.Services.WebMethodAttribute> и <xref:System.EnterpriseServices.ServicedComponent> метод имеют конфликтующие поведения и требования для контекста и потока транзакций, поведение метода будет неправильным в некоторых сценариях.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, удалите атрибут из <xref:System.EnterpriseServices.ServicedComponent> метод.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует. Не существует сценариев которых допустимо сочетание этих элементов.

## <a name="see-also"></a>См. также
 <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>



