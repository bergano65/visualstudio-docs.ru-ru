---
title: Настройка преобразования текста T4 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, API
- text templates, custom hosts
ms.assetid: 62cd9a3c-a6e1-4b29-93f5-f2a0cf47dc92
caps.latest.revision: 30
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 71cec79acfcc934f9ddd910006f32f5207b26c84
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654967"
---
# <a name="customizing-t4-text-transformation"></a>Настройка преобразования текста T4
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Текстовые шаблоны — это функция [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], позволяющая создавать программный код или другие текстовые файлы с помощью процесса преобразования. С помощью [!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)] можно расширить процесс преобразования шаблона по умолчанию, настроив обработчик директив текстового шаблона или узел текстового шаблона.

## <a name="in-this-section"></a>Содержание
 [Процесс преобразования текстовых шаблонов](../modeling/the-text-template-transformation-process.md) Описывает принцип работы преобразования текста и объясняет роль узла шаблона и процессоров директив.

 [Создание пользовательских обработчиков директив текстовых шаблонов T4](../modeling/creating-custom-t4-text-template-directive-processors.md) Процессор директивы работает с директивами в шаблоне, например `<#@template#>.` он выполняется во время компиляции шаблона и может загружать сборки и другие ресурсы. Он также может вставлять код, который будет загружать ресурсы во время выполнения. Определив собственный обработчик директив, можно уменьшить сложность шаблонов.

 [Вызов преобразования текста в расширении VS](../modeling/invoking-text-transformation-in-a-vs-extension.md) При написании расширения [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], например команды меню или обработчика событий, расширение может использовать службу текстовых шаблонов для преобразования любого текстового шаблона. Данные параметров можно передать в шаблон с помощью объекта Session и получить значения из шаблона с помощью директивы `<#@parameter#>`.

 [Обработка текстовых шаблонов с помощью пользовательского узла](../modeling/processing-text-templates-by-using-a-custom-host.md) При выполнении кода текстового шаблона узел предоставляет доступ к внешним файлам и состоянию приложения. Например, узел, выполняющий преобразования текста в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], может предоставить доступ к обозревателю решений. В нем также отображаются ошибки в окне сообщения об ошибке. Если вы хотите выполнять преобразования текста в другом контексте, можно определить собственный узел, предоставляющий доступ к службам, доступным в этом контексте.

 При написании расширения [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] рассмотрите возможность использования существующей службы преобразования текста вместо написания собственного узла. Дополнительные сведения см. [в разделе вызов преобразования текста в расширении VS](../modeling/invoking-text-transformation-in-a-vs-extension.md).

## <a name="reference"></a>Справочник
 [Написание текстового шаблона T4](../modeling/writing-a-t4-text-template.md)

 Предоставляет синтаксис директив и управляющих блоков текстового шаблона.
