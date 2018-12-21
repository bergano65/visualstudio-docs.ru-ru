---
title: Добавление службы хранилища Azure с помощью подключенных служб в Visual Studio | Документация Майкрософт
description: Добавление хранилища Azure в приложение с помощью диалогового окна добавления подключенных служб Visual Studio
author: ghogen
manager: douge
assetId: 521ec044-ad4b-4828-8864-01decde2e758
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/26/2017
ms.author: ghogen
ms.openlocfilehash: 63b796d9c514602a40f15b5725c07b1b89787df1
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002337"
---
# <a name="adding-azure-storage-by-using-visual-studio-connected-services"></a>Добавление службы хранилища Azure с помощью подключенных служб Visual Studio
С помощью Visual Studio, можно подключить любое из следующих в службу хранилища Azure с помощью **Добавление подключенных служб** диалоговое окно:

- C#облачная служба
- Серверная мобильная служба .NET
- Веб-сайта ASP.NET или службы
- Служба ASP.NET Core
- Служба веб-задания Azure 

Подключенные службы добавляет в проект все необходимые ссылки и код подключения и вносят соответствующие изменения в файлах конфигурации. 

После завершения **Добавление подключенных служб** диалоговое окно автоматически отображается документация с подробным описанием действий, необходимых для начала работы с хранилищем BLOB-объектов, очередей и таблиц.

## <a name="connect-to-azure-storage-using-the-connected-services-dialog"></a>Подключение к службе хранилища Azure с помощью диалогового окна подключенных служб
1. Откройте проект в Visual Studio

1. В **обозревателе решений**, щелкните правой кнопкой мыши **подключенных служб** узел и из контекстного меню и выберите **добавить подключенную службу**.
   
    ![Добавление Azure подключенной службы](./media/vs-azure-tools-connected-services-storage/IC796702.png)

1. В **подключенных служб** выберите **Облачное хранилище в службе хранилища Azure**.
   
    ![Добавление хранилища Azure](./media/vs-azure-tools-connected-services-storage/add-azure-storage.png)

1. В **хранилища Azure** диалоговое окно, выберите существующую учетную запись хранения и выберите **добавить**.
   
    Если вам нужно создать учетную запись хранения, перейдите к следующему шагу. В противном случае перейдите к шагу 6.
    
    ![Добавить существующую учетную запись хранения в проект](./media/vs-azure-tools-connected-services-storage/select-azure-storage-account.png)

1. Чтобы создать учетную запись хранения: 
   
   1. Выберите **создать учетную запись хранения** в нижней части диалогового окна.

   1. Заполните **создать учетную запись хранения** диалоговое окно, а затем выберите **создать**.
      
       ![Новую учетную запись хранения Azure](./media/vs-azure-tools-connected-services-storage/create-storage-account.png)
      
   1. Когда **хранилища Azure** отображается диалоговое окно, учетная запись хранения появится в списке. Выберите новую учетную запись хранения в списке и выберите **добавить**.

1. Подключенная служба хранилища появится в разделе **ссылок на службы** узле проекта.
   
## <a name="how-your-project-is-modified"></a>Как проект изменен
Если вы закроете диалоговое окно, Visual Studio добавляет ссылки и изменяет определенные файлы конфигурации. Конкретные изменения зависят от типа проекта: 

- Проект ASP.NET — [произошедшее — проекты ASP.NET](http://go.microsoft.com/fwlink/p/?LinkId=513126)
- Проект ASP.NET Core — [произошедшее — проекты ASP.NET 5](http://go.microsoft.com/fwlink/p/?LinkId=513124) 
- Проект облачной службы (веб-ролей и рабочих ролей) - [произошедшее — проекты облачных служб](http://go.microsoft.com/fwlink/p/?LinkId=516965)
- Проект веб-задания - [произошедшее — проекты веб-задания](/azure/visual-studio/vs-storage-webjobs-what-happened)

## <a name="next-steps"></a>Следующие шаги
- [Форум MSDN: Служба хранилища Azure](https://social.msdn.microsoft.com/forums/azure/home?forum=windowsazuredata)
- [Блог группы разработчиков хранилища Microsoft Azure](http://blogs.msdn.com/b/windowsazurestorage/)
- [Документация по хранилищу Azure](https://docs.microsoft.com/azure/storage/)
