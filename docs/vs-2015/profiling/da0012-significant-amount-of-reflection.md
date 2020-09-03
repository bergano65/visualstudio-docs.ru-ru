---
title: DA0012. Слишком много вызовов метода Reflection | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DAReflection
- vs.performance.12
- vs.performance.rules.DA0012
- vs.performance.DA0011
ms.assetid: c92a1d76-21fa-426e-8b1b-a3c08e9bcbca
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 54626c07fb8d15f585e800f03911dd465395d795
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850261"
---
# <a name="da0012-significant-amount-of-reflection"></a>DA0012. Слишком много вызовов метода Reflection
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Идентификатор правила | DA0012 |  
| Категория |. Использование NET Framework |  
| Методы профилирования | Выборка |  
| Сообщение | Возможно, используется отражение слишком часто. Это ресурсоемкая операция. |  
| Тип правила | Предупреждение |  
  
## <a name="cause"></a>Причина:  
 Вызовы методов System.Reflection, таких как InvokeMember и GetMember, или методов Type, таких как MemberInvoke, составляют значительную часть данных профилирования. По возможности рекомендуется заменить эти методы ранней привязкой к методам зависимых сборок.  
  
## <a name="rule-description"></a>Описание правила  
 Метод Reflection является гибким средством платформы .NET Framework, который может использоваться для выполнения позднего связывания приложения с зависимыми сборками времени выполнения или для создания и динамического выполнения новых типов во время выполнения. Тем не менее, применение этого метода может снизить производительность, если он вызывается слишком часто или внутри цикла с большим числом итераций.  
  
 Дополнительные сведения см. в подразделе [Отражение и позднее связывание](https://msdn.microsoft.com/library/ms998547.aspx#scalenetchapt05_topic31) раздела "Глава 5. Улучшение производительности управляемого кода" в томе "Повышение производительности и масштабируемости приложений .NET" библиотеки шаблонов и практических рекомендаций Microsoft на веб-сайте MSDN.  
  
## <a name="how-to-investigate-a-warning"></a>Изучение причин предупреждения  
 Дважды щелкните сообщение в окне "Список ошибок", чтобы перейти к представлению [Сведения о функциях](../profiling/function-details-view.md) данных профилирования. Проверьте вызовы функций методов System.Type и System.Reflection, чтобы найти участки программы, в которых наиболее часто используется API .NET Reflection. Избегайте использования методов, возвращающих метаданные. Если важна производительность приложения, следует избегать позднего связывания и динамического создания типов во время выполнения.
