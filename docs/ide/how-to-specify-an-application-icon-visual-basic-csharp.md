---
title: Практическое руководство. Задание значка приложения (Visual Basic, C#)
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- icons [Visual Studio], application
- application properties [Visual Studio], icons
- application icons [Visual Studio]
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 1e137eda77f1807b80409872d9fe0c2966df2a41
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656605"
---
# <a name="how-to-specify-an-application-icon-visual-basic-c"></a>Практическое руководство. Задание значка приложения (Visual Basic, C#)

Свойство `Icon` проекта указывает файл значка (*ICO*), который будет отображаться для скомпилированного приложения в **проводнике** и на панели задач Windows.

Доступ к свойству `Icon` можно получить в панели **Приложение** **конструктора проектов**. Оно содержит список значков, которые были добавлены в проект как ресурсы или файлы содержимого.

> [!NOTE]
> После задания свойства значка для приложения можно также задать свойство `Icon` каждого **окна** или **формы** в приложении. Сведения о значках окон для автономных приложений Windows Presentation Foundation (WPF) см. в разделе о свойстве <xref:System.Windows.Window.Icon%2A>.

## <a name="to-specify-an-application-icon"></a>Указание значка приложения

1. В **обозревателе решений** выберите узел проекта (не узел **Решение**).

1. В строке меню выберите **Проект** > **Свойства**.

1. Когда откроется **Конструктор проектов**, выберите вкладку **Приложение**.

1. **(Visual Basic)** &mdash;В списке **Значок** выберите файл значка (*ICO*).

    **C#** &mdash;Рядом со списком **Значок** нажмите кнопку **\<Обзор... >** , а затем перейдите в расположение файла значка.

## <a name="see-also"></a>См. также

- [Страница "Приложение" в конструкторе проектов (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
- [Страница "Приложение" в конструкторе проектов (C#)](../ide/reference/application-page-project-designer-csharp.md)