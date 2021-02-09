---
title: Как создать приемник событий | Документация Майкрософт
description: Создайте приемник событий, чтобы вы могли ответить, когда пользователь взаимодействует с элементами SharePoint, такими как списки или элементы списка.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 1943bd8a652a88d218912ab0fc0f6227bf83bc95
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885707"
---
# <a name="how-to-create-an-event-receiver"></a>Практическое руководство. Создание приемника событий
  Создавая *приемники событий*, вы можете ответить, когда пользователь взаимодействует с элементами SharePoint, такими как списки или элементы списка. Например, код приемника событий может сработать, если пользователь изменит календарь или удалит имя из списка контактов. Следуя описанным в этом разделе процедурам, можно узнать, как добавить приемник событий в экземпляр списка.

 Для выполнения этих шагов требуется установить [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] и иметь поддерживаемые версии Windows и SharePoint. Поскольку для этого примера требуется проект SharePoint, необходимо также выполнить процедуру, описанную в разделе [Пошаговое руководство. Создание столбца сайта, типа содержимого и списка для SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md).

## <a name="adding-an-event-receiver"></a>Добавление приемника событий
 Проект, созданный в [пошаговом руководстве: Создание столбца сайта, типа содержимого и списка для SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) , включает пользовательские столбцы сайта, Пользовательский список и тип содержимого. В следующей процедуре вы развернете этот проект, добавив простой обработчик событий (приемник событий) в экземпляр списка, чтобы продемонстрировать, как управлять событиями, происходящими в таких элементах SharePoint, как списки.

#### <a name="to-add-an-event-receiver-to-the-list-instance"></a>Добавление приемника событий в экземпляр списка

1. Откройте проект, созданный в [разделе Пошаговое руководство: Создание столбца сайта, типа содержимого и списка для SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md).

2. В **Обозреватель решений** выберите узел проекта SharePoint с именем **курс**.

3. В строке меню выберите **Проект** > **Добавить новый элемент**.

4. В **Visual C#** или **Visual Basic** разверните узел **SharePoint** , а затем выберите элемент **2010** .

5. В области **шаблоны** выберите **приемник событий**, назовите его **TestEventReceiver1**, а затем нажмите кнопку **ОК** .

     Откроется **Мастер настройки SharePoint** .

6. В списке **какой тип приемника событий вам нужен?** выберите **события элемента списка**.

7. В списке **какой элемент должен быть источником событий?** выберите **пациентов (клиник\патиентс)**.

8. В списке **обработайте следующие события** установите флажок рядом с **элементом добавлен**, а затем нажмите кнопку **Готово** .

     Файл кода для нового приемника событий содержит единственный метод с именем `ItemAdded` . На следующем шаге вы добавите код в этот метод, чтобы каждый контакт был назван Скотт Иванов по умолчанию.

9. Замените существующий `ItemAdded` метод следующим кодом, а затем нажмите клавишу **F5** :

     [!code-csharp[SP_EventReceiver#1](../sharepoint/codesnippet/CSharp/CustomField1/TestEventReceiver1/TestEventReceiver1.cs#1)]
     [!code-vb[SP_EventReceiver#1](../sharepoint/codesnippet/VisualBasic/CustomField1_VB/EventReceiver1/EventReceiver1.vb#1)]

     Код выполнится, и в веб-браузере откроется сайт SharePoint.

10. На панели быстрого запуска выберите ссылку **пациентов** , а затем щелкните ссылку **Добавить новый элемент** .

     Откроется форма ввода новых элементов.

11. Введите данные в поля, а затем нажмите кнопку **сохранить** .

     После нажатия кнопки **сохранить** столбец **имя пациента** автоматически обновляется до имени Скотта Иванов.

## <a name="see-also"></a>См. также раздел

- [Разработка решений SharePoint](../sharepoint/developing-sharepoint-solutions.md)