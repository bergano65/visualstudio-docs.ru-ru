---
title: Как реализовать операцию Windows Communication Foundation контракта (устаревшая) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: d6aeb20e-fac8-4a9d-bd26-ae78bef96b41
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1f6f54e781dfae15b4b1c1159d73ac3495b35c21
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72603867"
---
# <a name="how-to-implement-a-windows-communication-foundation-contract-operation-legacy"></a>Как реализовать операцию контракта Windows Communication Foundation (для прежних версий)
В этом разделе описывается реализация операции контракта [!INCLUDE[indigo1](../includes/indigo1-md.md)] с помощью средства [!INCLUDE[wfd1](../includes/wfd1-md.md)] прежних версий, ориентированного на работу с [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] или [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 После перетаскивания действия **ReceiveActivity** из области элементов в рабочую область конструктора рабочих процессов вы создадите новый [!INCLUDE[indigo2](../includes/indigo2-md.md)]ный контракт или импортируете существующий контракт и реализуем операции. Вы выбираете и/или создаете контракт и его операции в [диалоговом окне Выбор операции (прежние версии)](../workflow-designer/choose-operation-dialog-box-legacy.md).

### <a name="to-implement-a-wcf-contract-operation"></a>Реализация операции контракта WCF

1. Дважды щелкните действие **ReceiveActivity** в конструкторе или нажмите кнопку с многоточием рядом со свойством **ServiceOperationInfo** на панели **свойств** .

2. Выполните одно из следующих действий.

   - Щелкните **Добавить контракт** в правом верхнем углу диалогового окна. Будет создан новый контракт [!INCLUDE[indigo2](../includes/indigo2-md.md)] и операция.

      \- или -

   - Щелкните **Импорт** в правом верхнем углу диалогового окна. Откроется [диалоговое окно "Обзор и выбор типа .NET" (устаревшая)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md) . Найдите сборку или проект, который содержит нужный контракт. Выберите контракт и нажмите кнопку **ОК**.

     После создания или импортирования контракта к нему можно добавить новые операции. Чтобы добавить новую операцию, выберите контракт и щелкните **добавить операцию** в правом верхнем углу диалогового окна. После завершения добавления операций перейдите к шагу 3.

3. Выберите операцию, которую необходимо связать с действием **ReceiveActivity** . Управлять определением операции можно с помощью изменения имени операции, параметров, свойств и параметров разрешения.

    Чтобы изменить имя, введите новое имя в текстовое поле **имя операции** .

    Перейдите на вкладку **Параметры** , чтобы получить доступ к параметрам операции. Можно изменить имя, тип, направление параметра, а также добавить или удалить параметры из операции.

    Перейдите на вкладку **Свойства** , чтобы получить доступ к уровню защиты операций и поддерживаемым функциям обмена сообщениями операции.

    Перейдите на вкладку **разрешения** , чтобы указать группы, которым разрешено реализовывать эту операцию.

4. Нажмите кнопку **ОК** , и действие **ReceiveActivity** отобразит имя операции для операции, которую она реализует.

5. Поместите действия рабочего процесса, которые будут использоваться для реализации этой операции, в рамках действия **ReceiveActivity** .

## <a name="see-also"></a>См. также раздел
 [Диалоговое окно «Выбор операции» (устаревшая)](../workflow-designer/choose-operation-dialog-box-legacy.md) как вызывать [устаревшие действия](../workflow-designer/legacy-workflow-activities.md) [по контракту WCF (устаревшие).](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)