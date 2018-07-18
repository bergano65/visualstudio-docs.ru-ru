---
title: Конструктор рабочих процессов - конструктор действия TransactedReceiveScope
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.ServiceModel.Activities.TransactedReceiveScope.UI
ms.assetid: 7ca93aad-4e83-4d81-90f4-998ee114d9b6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c7f5c4cd48cc98d58da278ac53c1a829d15c43cd
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31976856"
---
# <a name="transactedreceivescope-activity-designer"></a>Конструктор действия TransactedReceiveScope

**TransactedReceiveScope** конструктор используется для создания и настройки <xref:System.ServiceModel.Activities.TransactedReceiveScope> действия.

## <a name="the-transactedreceivescope-activity"></a>Действие TransactedReceiveScope

Действие <xref:System.ServiceModel.Activities.TransactedReceiveScope> позволяет передать транзакцию в состав транзакций сервера, созданных рабочим процессом или диспетчером.

### <a name="using-the-transactedreceivescope-activity-designer"></a>Использование конструктора операций TransactedReceiveScope
 **TransactedReceiveScope** конструктора действий можно найти в **обмен сообщениями** категории **элементов**, который нажав **элементов**  вкладку в конструкторе рабочих процессов (либо выберите **инструментов** из **представление** меню или сочетание клавиш CTRL + ALT + X.)

 **TransactedReceiveScope** конструктора можно перетащить из **элементов** и удалена на поверхности конструктора рабочих процессов, везде, где обычно размещаются действия. При этом создается <xref:System.ServiceModel.Activities.TransactedReceiveScope> действия по умолчанию **DisplayName** для TransactedReceiveScope. <xref:System.Activities.Activity.DisplayName%2A> Можно изменить в заголовке **TransactedReceiveScope** конструктора или в **DisplayName** поле сетки свойств.

 **TransactedReceiveScope** конструктор содержит **запроса** и **текст** поля. Они используются для настройки свойства <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>, задающего действие <xref:System.ServiceModel.Activities.Receive> и свойство <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>, которое задает другое действие <xref:System.Activities.Activity>. Свойство <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> создает транзакцию. Затем транзакция определяется как внешняя для области <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>, так что любое действие в области выполняется внутри данной транзакции.

### <a name="the-transactedreceivescope-properties"></a>Свойства TransactedReceiveScope
 В следующей таблице показаны свойства <xref:System.ServiceModel.Activities.TransactedReceiveScope> и описано их использование в конструкторе. Эти <xref:System.Activities.Activity.DisplayName%2A> свойство можно изменить в таблице свойств или в рабочей области конструктора рабочих процессов, но остальные следует изменять в области конструктора.

|Имя свойства|Обязательно|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Необязательное понятное имя действия <xref:System.ServiceModel.Activities.TransactedReceiveScope>. Значение по умолчанию - TransactedReceiveScope.<br /><br /> Для имени <xref:System.Activities.Activity.DisplayName%2A> нет жестких требований, однако лучше всего использовать отображаемое имя.|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>|Да|Удаляет <xref:System.ServiceModel.Activities.Receive> действия в **запроса** блок в области конструктора операций.|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>|False|Удаляет <xref:System.Activities.Activity> в **текст** блок в области конструктора операций.|

## <a name="see-also"></a>См. также

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Отправить](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)