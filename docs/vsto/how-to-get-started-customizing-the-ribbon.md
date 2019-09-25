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
ms.openlocfilehash: a9b0f1ef704f5dd1426374e23806e5950ed5f6bb
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255862"
---
# <a name="how-to-get-started-customizing-the-ribbon"></a>Практическое руководство. Приступая к настройке ленты
  Чтобы настроить ленту Microsoft Office приложения, добавьте элемент **Лента (визуальный конструктор)** или **Лента (XML)** в проект Office.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-add-a-ribbon-to-a-project"></a>Добавление ленты в проект

1. В меню **проект** выберите команду **Добавить новый элемент**.

2. В диалоговом окне **Добавление нового элемента** выберите элемент **Лента (визуальный конструктор)** или **Лента (XML)** . Дополнительные сведения об этих шаблонах см. в статье [Общие сведения о ленте](../vsto/ribbon-overview.md).

3. В поле **имя** введите имя элемента ленты.

    Имена не могут содержать следующие символы:

   - Фунт (#)

   - Процент (%)

   - Амперсанд (&)

   - Звездочка (*)

   - Вертикальная черта (|)

   - Обратная косая черта (\\)

   - Двоеточие (:)

   - Двойные кавычки (")

   - Меньше (\<)

   - Больше (>)

   - Вопросительный знак (?)

   - Косая черта (/)

   - Начальные или конечные пробелы ("")

   - Имена, зарезервированные для Windows или DOS, такие как ("NUL", "AUX", "Con", "COM1", "LPT1" и т. д.)

4. Нажмите кнопку **ОК**.

   Элемент Лента появится в **Обозреватель решений**. Дополнительные сведения о дальнейших действиях см. в разделе [Лента Overview](../vsto/ribbon-overview.md).

## <a name="see-also"></a>См. также
- [Доступ к ленте во время выполнения](../vsto/accessing-the-ribbon-at-run-time.md)
- [Конструктор лент](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Пошаговое руководство: Создание настраиваемой вкладки с помощью конструктора лент](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Пошаговое руководство: Создание настраиваемой вкладки с помощью XML-ленты](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
