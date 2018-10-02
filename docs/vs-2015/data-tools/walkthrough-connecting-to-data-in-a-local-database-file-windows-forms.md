---
title: 'Пошаговое руководство: Подключение к данным в файл локальной базы данных (Windows Forms) | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- databases, connecting to
- local data, SQL Express
- SQL Express, walkthroughs
- SQL Express, connecting
- data [Visual Studio], local
- data [Visual Studio], connecting to SQL Express
ms.assetid: 5e16b7da-3fdc-4e69-bdb4-e8e700481811
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 9b2d17c5ed86e37d3c674ef9238702cd8557a90f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47570801"
---
# <a name="walkthrough-connecting-to-data-in-a-local-database-file-windows-forms"></a>Пошаговое руководство. Подключение к данным в локальном файле базе данных (Windows Forms)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Можно быстро и легко отображать данные из локального файла базы данных в приложении. Для этого требуется создать набор данных и добавить в приложение элементы управления с привязкой к данным. В этом пошаговом руководстве, как отображать данные из файла локальной базы данных, который вы создали, выполнив действия, описанные в [создать базу данных SQL с помощью конструктора](../data-tools/create-a-sql-database-by-using-a-designer.md). Мы создадим проект Windows Forms, подключимся к базе данных и определим отображение данных из таблицы Customers в таблице данных в форме приложения.  
  
 При создании базы данных в Visual Studio 2013 для доступа к файлу базы данных (MDF) в SQL Server 2012 используется обработчик SQL Server Express LocalDB. В более ранних версиях Visual Studio для доступа к файлу базы данных (MDF) используется обработчик SQL Server Express. См. в разделе [Общие сведения о локальных данных](../data-tools/local-data-overview.md).  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
 В этом пошаговом руководстве рассматриваются следующие задачи:  
  
-   [Создание и настройка набора данных](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md#BKMK_CreateDataset)  
  
-   [Добавление элементов управления с привязкой к данным](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md#BKMK_AddCtrls)  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения этого пошагового руководства, вам нужен доступ к базе данных SampleDatabase.mdf, созданной [создать базу данных SQL с помощью конструктора](../data-tools/create-a-sql-database-by-using-a-designer.md).  
  
##  <a name="BKMK_CreateDataset"></a> Создание и настройка набора данных  
  
#### <a name="to-create-and-configure-a-dataset"></a>Как создать и настроить набор данных  
  
1.  Создайте проект Windows Forms и назовите его **ConnectLocalData**.  
  
     См. в разделе [клиентских приложений](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
2.  Если **источников данных** окно не отображается, нажмите сочетание клавиш Shift + Alt + D или в строке меню выберите **представление**, **Other Windows**, **Показать источники данных**.  
  
3.  В **источников данных** окно, выберите **добавить новый источник данных** ссылку.  
  
     В **мастер настройки источника данных**, выберите **Далее** кнопку два раза, чтобы принять параметры по умолчанию.  
  
4.  На **Выбор подключения к данным** выберите **новое подключение** кнопки.  
  
     **Выбор источника данных** откроется диалоговое окно.  
  
5.  В **источника данных** выберите **Microsoft SQL Server Database File**, а затем выберите **Продолжить** кнопки.  
  
     **Добавить подключение** откроется диалоговое окно.  
  
6.  В **имя файла базы данных** укажите файл, который создается в ходе выполнения [создать базу данных SQL с помощью конструктора](../data-tools/create-a-sql-database-by-using-a-designer.md), или выберите **Обзор** кнопку, а затем найдите Этот файл.  
  
     По умолчанию файл находится в пользователи\\*Ваша_учетная_запись*\Documents\Visual Studio *версии*\Projects\SampleDatabaseWalkthrough\SampleDatabaseWalkthrough.  
  
7.  В разделе **вход на сервер**, примите значения по умолчанию, выберите **ОК** кнопку, а затем выберите **Далее** кнопки.  
  
    > [!NOTE]
    >  При подключении к файлу локальной базы данных можно создать копию базы данных в проекте или подключиться к файлу базы данных в текущем расположении. См. в разделе [как: управление локальными файлами данных в проекте](../data-tools/how-to-manage-local-data-files-in-your-project.md).  
  
8.  В появившемся диалоговом окне, выберите **Да** скопировать файл базы данных в проект.  
  
9. На **сохранение подключения в файле конфигурации приложения** выберите **Далее** кнопки.  
  
10. На **Выбор объектов базы данных** странице, разверните узел **таблиц** выберите **клиентов** и **заказы** флажки, а затем Выберите **Готово** кнопки.  
  
     **SampleDatabaseDataSet** добавляется в проект и **клиентов** и **заказы** таблицы отображаются в **источников данных** окна.  
  
##  <a name="BKMK_AddCtrls"></a> Добавление элементов управления с привязкой к данным  
  
#### <a name="to-add-data-bound-controls"></a>Чтобы добавить элементы управления с привязкой к данным  
  
1.  Переместите главный **клиентов** узел из **источников данных** окна на **Form1**.  
  
     На форме появляются <xref:System.Windows.Forms.DataGridView> и полоса инструментов (<xref:System.Windows.Forms.BindingNavigator>) для перемещения по записям. Объект [SampleDatabaseDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource>, и <xref:System.Windows.Forms.BindingNavigator> отображаются в области компонентов.  
  
2.  Для запуска приложения и отображения данных, добавленных в предыдущем пошаговом руководстве, нажмите клавишу F5.  
  
3.  Выберите желтый значок добавления (![кнопка "Добавить" в форме Windows](../data-tools/media/addrecord.png "AddRecord")), добавьте запись клиента и затем сохраните изменения, щелкнув значок диска (![кнопку "Сохранить" в форме Windows](../data-tools/media/saveinwf.png "SaveInWF")).  
  
4.  Удалить запись, которую вы только что создали, выбрав его, а затем выберите красный значок удаления (![кнопки "Удалить" в форме Windows](../data-tools/media/deleterecord.png "DeleteRecord")).  
  
## <a name="next-steps"></a>Следующие шаги  
 Можно создать или изменить объекты в наборе данных, открыв источник данных в [Создание и изменение типизированных наборов DataSet](../data-tools/creating-and-editing-typed-datasets.md). Также можно добавить логику проверки в событие <xref:System.Data.DataTable.ColumnChanging> или <xref:System.Data.DataTable.RowChanging> таблиц набора данных. См. в разделе [проверки данных в наборах данных](../data-tools/validate-data-in-datasets.md).  
  
## <a name="see-also"></a>См. также  
 [Общие сведения о локальных данных](../data-tools/local-data-overview.md)   
 [Практическое: управление локальными файлами данных в проекте](../data-tools/how-to-manage-local-data-files-in-your-project.md)   
 [Привязка элементов управления Windows Forms к данным в Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Подключение к данным в Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Подготовка приложения для получения данных](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Выборка данных в приложение](../data-tools/fetching-data-into-your-application.md)   
 [Привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Редактирование данных в приложении](../data-tools/editing-data-in-your-application.md)   
 [Проверка данных](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Сохранение данных](../data-tools/saving-data.md)