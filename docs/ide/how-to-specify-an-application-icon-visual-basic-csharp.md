---
title: Практическое руководство. Задание значка приложения (Visual Basic, C#)
description: Сведения о том, как использовать свойство Icon для указания значка, отображаемого проводником и панелью задач Windows, для скомпилированного приложения.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- icons [Visual Studio], application
- application properties [Visual Studio], icons
- application icons [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 34405fd52b49e89c2fa0fc95ec1268448bad3061
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95596915"
---
# <a name="how-to-specify-an-application-icon-visual-basic-c"></a>Практическое руководство. Задание значка приложения (Visual Basic, C#)

Свойство `Icon` проекта указывает файл значка (*ICO*), который будет отображаться для скомпилированного приложения в **проводнике** и на панели задач Windows.

Доступ к свойству `Icon` можно получить в панели **Приложение** **конструктора проектов**. Оно содержит список значков, которые были добавлены в проект как ресурсы или файлы содержимого.

> [!NOTE]
> После задания свойства значка для приложения можно также задать свойство `Icon` каждого **окна** или **формы** в приложении. Сведения о значках окон для автономных приложений Windows Presentation Foundation (WPF) см. в разделе о свойстве <xref:System.Windows.Window.Icon%2A>.

## <a name="to-specify-an-application-icon"></a>Указание значка приложения

1. В **обозревателе решений** выберите узел проекта (не узел **Решение**).

1. В строке меню щелкните **Проект** > **Свойства**.

1. Когда откроется **Конструктор проектов**, выберите вкладку **Приложение**.

1. **(Visual Basic)** &mdash;В списке **Значок** выберите файл значка (*ICO*).

    **C#** &mdash;Рядом со списком **Значок** нажмите кнопку **\<Browse...>** , а затем перейдите в расположение файла значка.

## <a name="see-also"></a>См. также

- [Страница "Приложение" в конструкторе проектов (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
- [Страница "Приложение" в конструкторе проектов (C#)](../ide/reference/application-page-project-designer-csharp.md)
