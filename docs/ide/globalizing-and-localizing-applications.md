---
title: Глобализация и локализация приложений
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- globalization [Visual Studio]
- Visual Basic code, international applications
- C#, international applications
- localization [Visual Studio]
- world-ready applications
- international applications [Visual Studio]
ms.assetid: 4d9815ae-3e80-4b4d-933d-f8309aee18d5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6f08ad869e1a8d06a8a29325c2cbeb723734c6f2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53991075"
---
# <a name="globalizing-and-localizing-applications"></a>Глобализация и локализация приложений

Если вы планируете распространять приложения для международного использования, следует учесть несколько аспектов на этапах проектирования и разработки. Даже если пока у вас нет подобных планов, небольшие заблаговременные приготовления помогут значительно облегчить смену курса в будущих версиях приложения. Службы, встроенные в [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], упрощают разработку отдельного приложения, которое можно адаптировать для разных языков и региональных параметров с помощью управляемой разработки в Visual Studio.

## <a name="resources"></a>Ресурсы

 Система Visual Studio изначально ориентирована на упрощение разработки международных версий за счет применения служб, встроенных в [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. В следующих статьях описаны доступные в Visual Studio возможности по интернационализации.

 В статье [Знакомство с международными приложениями на платформе .NET Framework](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md) описаны основные принципы разработки программного обеспечения для международного рынка с использованием Visual Studio и [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].

 В статье о [локализации приложений](../ide/localizing-applications.md) содержатся ссылки на сведения о настройке приложений для заданного языка и заданного набора региональных параметров.

 В статье о [глобализации приложений](../ide/globalizing-applications.md) содержатся ссылки на страницы, посвященные созданию приложений, которые поддерживают несколько языков и региональных параметров.

## <a name="see-also"></a>См. также

- В статье [Рекомендации по разработке международных приложений](/dotnet/standard/globalization-localization/best-practices-for-developing-world-ready-apps) содержатся сведения о программировании для международной аудитории, в частности рассматриваются вопросы конструирования и терминологии.
- В [обзоре библиотек классов](/dotnet/standard/class-library-overview) описаны классы, интерфейсы и типы значений, которые облегчают и оптимизируют процесс разработки, а также обеспечивают доступ к функциям системы.
- В <xref:System.Globalization> описаны классы в этом пространстве имен, определяющие сведения, которые относятся к языку и региональным параметрам, такие как язык, страна или регион, используемые календари, шаблоны форматирования дат, денежных единиц и чисел, а также порядок сортировки строк.
- В <xref:System.Resources> описаны классы и интерфейсы в этом пространстве имен, позволяющие разработчикам создавать различные ресурсы для конкретного языка и региональных параметров, используемые в приложениях, сохранять эти ресурсы и управлять ими.