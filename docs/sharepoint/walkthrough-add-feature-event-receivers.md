---
title: 'Пошаговое руководство: Добавление приемников событий компонентов | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, advanced packaging tools
- SharePoint development in Visual Studio, event receivers
- SharePoint development in Visual Studio, feature event receivers
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: cda3967d0fc95fdd8f28503f209a5f2208d07031
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-add-feature-event-receivers"></a>Пошаговое руководство. Добавление приемников событий компонентов
  Приемников событий компонентов, методы, которые выполняются при возникновении одного из следующих событий, связанных с компонент в SharePoint:  
  
-   Компонент установлен.  
  
-   Компонент активирован.  
  
-   Отключение компонента.  
  
-   Удаление компонента.  
  
 В этом пошаговом руководстве показано, как добавить приемник событий компонентов в проекте SharePoint. Он демонстрирует следующие задачи:  
  
-   Создание пустого проекта с приемником событий компонента.  
  
-   Обработка **FeatureDeactivating** метод.  
  
-   Чтобы добавить объявление в список объявлений с помощью объектной модели проекта SharePoint.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Предварительные требования  
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.  
  
-   Поддерживаемые редакции Microsoft Windows и SharePoint. Дополнительные сведения см. в разделе [требования к разработке решений SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
## <a name="creating-a-feature-event-receiver-project"></a>Создание проекта приемника событий компонента  
 Сначала создайте проект, содержащий приемника событий компонента.  
  
#### <a name="to-create-a-project-with-a-feature-event-receiver"></a>Создание проекта с приемником событий компонента  
  
1.  В строке меню выберите **файл**, **New**, **проекта** для отображения **новый проект** диалоговое окно.  
  
2.  Разверните **SharePoint** узел в рамках одного **Visual C#** или **Visual Basic**, а затем выберите **2010** узла.  
  
3.  В **шаблоны** области, выберите **проект SharePoint 2010** шаблона.  
  
     Этот тип проекта предназначен для приемников событий компонентов, поскольку для них не существует шаблона проекта.  
  
4.  В **имя** введите **FeatureEvtTest**, а затем выберите **ОК** кнопку, чтобы отобразить **мастер настройки SharePoint**.  
  
5.  На **Укажите сайт и уровень безопасности для отладки** введите URL-адрес сайта сервера SharePoint, к которому требуется добавить новый элемент настраиваемого поля или использовать расположение по умолчанию (http://\<*системы имя*> /).  
  
6.  В **Какова степень доверия для этого решения SharePoint?** выберите **развернуть как решение фермы** переключатель.  
  
     Дополнительные сведения об изолированных решениях и решений фермы см. в разделе [замечания об изолированных решениях](../sharepoint/sandboxed-solution-considerations.md).  
  
7.  Выберите **Готово** кнопку, а затем Обратите внимание, что компонент с именем Feature1 находится в разделе **функции** узла.  
  
## <a name="adding-an-event-receiver-to-the-feature"></a>Добавление приемника событий в компонент  
 Затем добавить приемник событий в компонент и добавьте код, который выполняется после отключения компонента.  
  
#### <a name="to-add-an-event-receiver-to-the-feature"></a>Чтобы добавить приемник событий в компонент  
  
1.  Откройте контекстное меню для узла компонентов, а затем выберите **добавить компонент** Чтобы создать компонент.  
  
2.  В разделе **функции** узел, откройте контекстное меню для **Feature1**и нажмите кнопку **добавить приемник событий** для добавления приемника событий в компонент.  
  
     При этом добавляется файл кода в компонент Feature1. В этом случае она называется Feature1.EventReceiver.cs или Feature1.EventReceiver.vb, в зависимости от языка разработки проекта.  
  
3.  Если проект написан на [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)], добавьте следующий код в начало приемника событий, если он еще не находится там:  
  
     [!code-csharp[SP_FeatureEvt#1](../sharepoint/codesnippet/CSharp/featureevttest2/features/feature1/feature1.eventreceiver.cs#1)]  
  
4.  Класс приемника событий содержит несколько закомментированных методов, действующих как события. Замените **FeatureDeactivating** метод со следующими:  
  
     [!code-vb[SP_FeatureEvt#2](../sharepoint/codesnippet/VisualBasic/featureevt2vb/features/feature1/feature1.eventreceiver.vb#2)]
     [!code-csharp[SP_FeatureEvt#2](../sharepoint/codesnippet/CSharp/featureevttest2/features/feature1/feature1.eventreceiver.cs#2)]  
  
## <a name="testing-the-feature-event-receiver"></a>Тестирование приемника событий компонента  
 Затем отключите компонент, чтобы протестировать ли **FeatureDeactivating** метод выводит объявление списка извещений SharePoint.  
  
#### <a name="to-test-the-feature-event-receiver"></a>Тестирование приемника событий компонента  
  
1.  Установите для параметра проекта **активная конфигурация развертывания** свойства **без активации**.  
  
     Задание этого свойства предотвращает возможность активации в SharePoint и позволит выполнить отладку приемников событий компонентов. Дополнительные сведения см. в разделе [отладка решений SharePoint](../sharepoint/debugging-sharepoint-solutions.md).  
  
2.  Выберите **F5** ключ для запуска проекта и его развертывания в SharePoint.  
  
3.  В верхней части веб-страницы SharePoint, откройте **действия сайта** меню, а затем выберите **параметры сайта**.  
  
4.  В разделе **действия сайта** раздел **параметры сайта** выберите **управление возможностями сайта** ссылку.  
  
5.  На **функции** выберите **активировать** рядом с **FeatureEvtTest Feature1** компонентов.  
  
6.  На **функции** выберите **деактивировать** рядом с **FeatureEvtTest Feature1** компонент и выберите **деактивировать этот компонент**  ссылку для подтверждения отключения компонента.  
  
7.  Выберите **Главная** кнопки.  
  
     Обратите внимание, что появилось объявление в **объявления** вывести после отключения компонента.  
  
## <a name="see-also"></a>См. также  
 [Как: Создание приемника событий](../sharepoint/how-to-create-an-event-receiver.md)   
 [Разработка решений SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  