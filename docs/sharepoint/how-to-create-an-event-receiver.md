---
title: Практическое руководство. Создание приемника событий | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.SPE.EventReceiver
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, event receivers
- event receivers [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bc42a92e1d7dcc73bb6bc0433da4e6a31d7fefb2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62966761"
---
# <a name="how-to-create-an-event-receiver"></a>Практическое руководство. Создание приемника событий
  Создав *приемников событий*, может отвечать, когда пользователь взаимодействует с элементами SharePoint, такие как списки или элементы списка. Например, код приемника событий может сработать, если пользователь изменит календарь или удалит имя из списка контактов. Следуя описанным в этом разделе процедурам, можно узнать, как добавить приемник событий в экземпляр списка.

 Для выполнения этих шагов требуется установить [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] и иметь поддерживаемые версии Windows и SharePoint. Так как в этом примере требуется проект SharePoint, необходимо также выполнить процедуру, описанную в разделе [Пошаговое руководство: Создание столбца сайта, тип содержимого и списка для SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md).

## <a name="adding-an-event-receiver"></a>Добавление приемника событий
 Проект, созданный в [Пошаговое руководство: Создание столбца сайта, тип содержимого и списка для SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) включает в себя пользовательские столбцы сайтов, пользовательский список и типом содержимого. В следующей процедуре этот проект будет дополнен путем добавления простого обработчика событий (приемника событий) в экземпляр списка, чтобы показать, как обрабатывать события, возникающие в элементах SharePoint, такие как списки.

#### <a name="to-add-an-event-receiver-to-the-list-instance"></a>Чтобы добавить приемник событий в экземпляр списка

1. Откройте проект, созданный в [Пошаговое руководство: Создание столбца сайта, тип содержимого и списка для SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md).

2. В **обозревателе решений**, выберите узел проекта SharePoint, которая называется **Clinic**.

3. В строке меню выберите **Проект** > **Добавить новый элемент**.

4. В группе **Visual C#** или **Visual Basic**, разверните **SharePoint** узел, а затем выберите **2010** элемента.

5. В **шаблоны** области выберите **приемника событий**, назовите его **TestEventReceiver1**, а затем выберите **ОК** кнопку.

     **Мастер настройки SharePoint** отображается.

6. В **тип приемника событий требуются?** выберите **события элемента списка**.

7. В **какой элемент должен быть источником событий?** выберите **Patients (Clinic\Patients)**.

8. В **обрабатывать следующие события** списке, установите флажок рядом с полем **добавлен элемент**и нажмите кнопку **Готово** кнопки.

     Файл кода для нового приемника событий содержит один метод с именем `ItemAdded`. На следующем шаге вы добавите код в этот метод, чтобы каждый контакту имя Scott Brown по умолчанию.

9. Замените существующий `ItemAdded` следующим кодом кода, а затем выберите **F5** ключ:

     [!code-csharp[SP_EventReceiver#1](../sharepoint/codesnippet/CSharp/CustomField1/TestEventReceiver1/TestEventReceiver1.cs#1)]
     [!code-vb[SP_EventReceiver#1](../sharepoint/codesnippet/VisualBasic/CustomField1_VB/EventReceiver1/EventReceiver1.vb#1)]

     Код выполнится, и в веб-браузере откроется сайт SharePoint.

10. На панели быстрого запуска выберите **пациентов** связать, а затем щелкните **Добавление нового элемента** ссылку.

     Откроется форма ввода новых элементов.

11. Введите данные в полях и нажмите **Сохранить** кнопки.

     После того как вы выберете **Сохранить** кнопки **Patient Name** столбца автоматически обновляет примет значение Scott Brown.

## <a name="see-also"></a>См. также

- [Разработка решений SharePoint](../sharepoint/developing-sharepoint-solutions.md)