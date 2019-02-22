---
title: Настройка ленты для Outlook
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Inspectors [Office development in Visual Studio]
- Outlook [Office development in Visual Studio], Ribbon
- customizing the Ribbon, about customizing the Ribbon
- custom Ribbon, about customizing the Ribbon
- Ribbon [Office development in Visual Studio], Outlook
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 58735a36afd48132f919e370da5e27fd0c42a0f0
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56614965"
---
# <a name="customize-a-ribbon-for-outlook"></a>Настройка ленты для Outlook
  При настройке ленты в Microsoft Office Outlook необходимо знать, где в приложении отображается настраиваемая лента. Outlook показывает ленту в пользовательском интерфейсе основного приложения и в окнах, открывающихся при выполнении пользователем определенных задач, таких как создание сообщений электронной почты. Эти окна приложения называются инспекторами.

 ![ссылка на видео](../vsto/media/playvideo.gif "ссылка на видео") демонстрационные видеоматериалы см. в разделе [инструкции: Использование конструктора ленты для настройки ленты в Outlook? ](http://go.microsoft.com/fwlink/?LinkID=130312).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="add-a-custom-ribbon-to-the-main-application-ui"></a>Добавление настраиваемой ленты в пользовательский Интерфейс основного приложения
 Пользовательский интерфейс основного приложения в Outlook называется проводником. Если вы используете **Лента (визуальный конструктор)** элемента, можно добавить ленту в проводник, щелкнув **RibbonType** ленты в **свойства** окне а затем выбрав **Microsoft.Outlook.Explorer**.

## <a name="assign-a-ribbon-to-an-inspector"></a>Назначение ленты инспектору
 Вы можете указать инспектор, который требуется настроить, выбрав тип ленты, соответствующий классу сообщений для инспектора.

 Если вы используете **Лента (визуальный конструктор)** , щелкните **RibbonType** ленты в **свойства** окна, а затем выберите один или несколько ленте идентификаторы из список значений.

 В проект можно добавить несколько лент. Если несколько лент имеют одинаковый идентификатор, переопределите метод `CreateRibbonExtensibilityObject` в классе `ThisAddin` проекта, чтобы указать, какую ленту следует отображать во время выполнения. Дополнительные сведения см. в разделе [Обзор ленты](../vsto/ribbon-overview.md). Дополнительные сведения о каждом типе ленты см. в технической статье [настройки ленты в Outlook 2007](/previous-versions/office/developer/office-2007/bb226712(v=office.12)).

## <a name="specify-the-ribbon-type-by-using-ribbon-xml"></a>Указание типа ленты с помощью XML-ленты
 Если вы используете **Лента (XML)** , проверьте значение *ribbonID* параметр в <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> метода и верните нужную ленту.

 Метод <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> автоматически создается средой Visual Studio в файле кода ленты. *RibbonID* параметр представляет собой строку, определяющую проводник или тип инспектора. Полный список возможных значений *ribbonID* параметр, см. в технической статье [настройки ленты в Outlook 2007](/previous-versions/office/developer/office-2007/bb226712(v=office.12)).

 В следующем примере кода показано, как показывать настраиваемую ленту только в инспекторе `Microsoft.Outlook.Mail.Compose`. Этот инспектор открывается, когда пользователь создает сообщение электронной почты. Отображаемая лента указывается в `GetResourceText()` метод, который создается в **ленты** класса. Дополнительные сведения о **ленты** , представлена в разделе [Ribbon XML](../vsto/ribbon-xml.md).

 [!code-csharp[Trin_RibbonOutlookBasic#1](../vsto/codesnippet/CSharp/Trin_RibbonOutlookBasic/Ribbon1.cs#1)]
 [!code-vb[Trin_RibbonOutlookBasic#1](../vsto/codesnippet/VisualBasic/Trin_RibbonOutlookBasic/Ribbon1.vb#1)]

## <a name="see-also"></a>См. также
- [Доступ к ленте во время выполнения](../vsto/accessing-the-ribbon-at-run-time.md)
- [Обзор ленты](../vsto/ribbon-overview.md)
- [Конструктор лент](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
