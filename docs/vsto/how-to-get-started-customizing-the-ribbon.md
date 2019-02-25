---
title: Практическое руководство. Приступая к настройке ленты
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom Ribbon, adding Ribbon to project
- Ribbon [Office development in Visual Studio], adding
- Ribbon [Office development in Visual Studio], customizing
- customizing the Ribbon, adding Ribbon to project
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 14c4ff1e8bf443351f835d74d44b49bbb61e0321
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56640120"
---
# <a name="how-to-get-started-customizing-the-ribbon"></a>Практическое руководство. Приступая к настройке ленты
  Чтобы настроить ленту приложения Microsoft Office, добавьте **Лента (визуальный конструктор)** или **Лента (XML)** элемента в проект Office.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-add-a-ribbon-to-a-project"></a>Чтобы добавить ленты в проект

1. На **проекта** меню, щелкните **Добавление нового элемента**.

2. В **Добавление нового элемента** выберите **Лента (визуальный конструктор)** или **Лента (XML)**. Дополнительные сведения об этих шаблонах см. в разделе [Обзор ленты](../vsto/ribbon-overview.md).

3. В **имя** введите имя для элемента ленты.

    Имена не могут содержать следующие символы:

   -   Знак решетки (#)

   -   Знак процента (%)

   -   Амперсанд (&)

   -   Звездочка (*)

   -   Вертикальная черта (|)

   -   Обратная косая черта (\\)

   -   Двоеточие (:)

   -   Двойные кавычки (")

   -   Меньше (\<)

   -   Больше (>)

   -   Вопросительный знак (?)

   -   Косая черта (/)

   -   Начальные и конечные пробелы ("")

   -   Имена, зарезервированные для Windows или DOS, например («nul», «aux», «con», «com1», «lpt1» и т. д.)

4. Нажмите кнопку **ОК**.

   Элемент ленты отобразится в **обозревателе решений**. Сведения о дальнейших действиях см. в разделе [Обзор ленты](../vsto/ribbon-overview.md).

## <a name="see-also"></a>См. также
- [Доступ к ленте во время выполнения](../vsto/accessing-the-ribbon-at-run-time.md)
- [Конструктор лент](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Пошаговое руководство: Создание настраиваемой вкладки с помощью конструктора лент](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Пошаговое руководство: Создание настраиваемой вкладки с помощью XML-ленты](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
