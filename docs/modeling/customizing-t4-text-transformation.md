---
title: "Настройка преобразования текста T4 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text templates, API
- text templates, custom hosts
ms.assetid: 62cd9a3c-a6e1-4b29-93f5-f2a0cf47dc92
caps.latest.revision: "28"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: 98d7efc90a07de02f255afe1a75d10fef749e88a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="customizing-t4-text-transformation"></a>Настройка преобразования текста T4
Текстовые шаблоны являются возможностью [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , которые позволяют создавать программный код или другие текстовые файлы посредством процесса преобразования. С помощью [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)], можно расширить процесс преобразования шаблона по умолчанию, настроив процессор директив текстового шаблона или основное приложение текстового шаблона.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Процесс преобразования текстового шаблона](../modeling/the-text-template-transformation-process.md)  
 Описано, как работает преобразование текста и роль основного приложения шаблона и процессоры директив.  
  
 [Создание пользовательских обработчиков директив для текстовых шаблонов T4](../modeling/creating-custom-t4-text-template-directive-processors.md)  
 Процессор директив обрабатывает директивы в шаблоне, такие как `<#@template#>.` он выполняется в процессе компиляции шаблона и может загружать сборки и другие ресурсы. Его можно также вставить код, который будет загружать ресурсы во время выполнения. Определив собственный процессор директив, можно уменьшить сложность шаблонов.  
  
 [Вызов преобразования текста в расширении VS](../modeling/invoking-text-transformation-in-a-vs-extension.md)  
 При создании [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] расширения, такими как меню команды или обработчика событий, расширение можно использовать службы текстовых шаблонов для преобразования любого текстового шаблона. Можно передать данные параметров в шаблон с помощью объекта сеанса и получить значения из шаблона с помощью `<#@parameter#>` директивы.  
  
 [Обработка текстовых шаблонов с помощью пользовательского хост-класса](../modeling/processing-text-templates-by-using-a-custom-host.md)  
 При выполнении кода текстового шаблона узел предоставляет доступ к внешним файлам и состояние приложения. Например, узел, выполняющее преобразование текста в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] может предоставлять доступ к обозревателю решений. Она также отображает ошибки в окне сообщения об ошибках. Если вы хотите выполнить преобразования текста в другом контексте, можно определить собственный узел, который предоставляет доступ к службам, доступным в этом контексте.  
  
 При создании [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] расширения, можно воспользоваться имеющейся службой преобразования текста, а не создавать собственный узел. Дополнительные сведения см. в разделе [вызов преобразования текста в расширении VS](../modeling/invoking-text-transformation-in-a-vs-extension.md).  
  
## <a name="reference"></a>Ссылка  
 [Написание текстового шаблона T4](../modeling/writing-a-t4-text-template.md)  
  
 Предоставляет синтаксис директив текстового шаблона и управляющие блоки.