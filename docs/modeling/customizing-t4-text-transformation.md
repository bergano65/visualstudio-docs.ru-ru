---
title: Настройка преобразования текста T4
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, API
- text templates, custom hosts
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: b3960d0e511ab42de2bd81765fb395d2e013a493
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31948851"
---
# <a name="customizing-t4-text-transformation"></a>Настройка преобразования текста T4

Текстовые шаблоны являются возможностью [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , которые позволяют создавать программный код или другие текстовые файлы посредством процесса преобразования. С помощью [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)], можно расширить процесс преобразования шаблона по умолчанию, настроив процессор директив текстового шаблона или основное приложение текстового шаблона.

## <a name="in-this-section"></a>В этом разделе
 [Процесс преобразования текстового шаблона](../modeling/the-text-template-transformation-process.md) описано, как работает преобразование текста и роль основного приложения шаблона и процессоры директив.

 [Создание процессоров директив шаблона текста T4 настраиваемый](../modeling/creating-custom-t4-text-template-directive-processors.md) директивы процессор директив обрабатывает в шаблоне, такие как `<#@template#>.` он выполняется в процессе компиляции шаблона и может загружать сборки и другие ресурсы. Его можно также вставить код, который будет загружать ресурсы во время выполнения. Определив собственный процессор директив, можно уменьшить сложность шаблонов.

 [Вызов преобразования текста в расширении VS](../modeling/invoking-text-transformation-in-a-vs-extension.md) при создании [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] расширения, такими как меню команды или обработчика событий, расширение можно использовать службы текстовых шаблонов для преобразования любого текстового шаблона. Можно передать данные параметров в шаблон с помощью объекта сеанса и получить значения из шаблона с помощью `<#@parameter#>` директивы.

 [Обработка текстовых шаблонов с помощью пользовательского хост-](../modeling/processing-text-templates-by-using-a-custom-host.md) при выполнении кода текстового шаблона узел предоставляет доступ к внешним файлам и состояние приложения. Например, узел, выполняющее преобразование текста в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] может предоставлять доступ к обозревателю решений. Она также отображает ошибки в окне сообщения об ошибках. Если вы хотите выполнить преобразования текста в другом контексте, можно определить собственный узел, который предоставляет доступ к службам, доступным в этом контексте.

 При создании [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] расширения, можно воспользоваться имеющейся службой преобразования текста, а не создавать собственный узел. Дополнительные сведения см. в разделе [вызов преобразования текста в расширении VS](../modeling/invoking-text-transformation-in-a-vs-extension.md).

## <a name="reference"></a>Ссылка

- [Запись текстового шаблона T4](../modeling/writing-a-t4-text-template.md) предоставляет синтаксис директив текстового шаблона и управляющие блоки.