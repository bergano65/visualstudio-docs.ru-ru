---
title: Элементы пользовательского интерфейса данных | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.data.tablemappings
- vs.datasource.choosebindingsourcedialog
- vs.datasource.choosedatasourceinstancedlg
- vs.data.editrelation
- DSD_EditMultiKey
- vs.datasource.RealtionBuilder
- vs.xmldesigner.editkey
- vs.xmldesigner.choosekey
- vs.data.generatedataset
- vs.data.configurationerror
- vs.data.DSD_MissingConnections_Message
- vs.datasource.choosedesigndatasourcedlg
- vs.data.datapreview
- vs.data.editforeignkeyconstraint
- vs.datasource.choosedataconectordialog
- vs.data.dataadapterpreview
- vs.data.configurationwizard
- vs.data.datapreviewdialog
- DSD_EditMultiKeyHelpID
- vs.data.advancedoptions
- vs.data.previewscript
- vs.data.datasourcelogin
- vs.syncdesigner.syncnowconflictiondialog
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- dialog boxes, data
- data [Visual Studio], dialog boxes
ms.assetid: 90943baf-5bd1-4eef-927f-f82485979fde
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: b699d44b8aa5b8c9e1e917e4e361414ff1a9afd4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47557643"
---
# <a name="data-user-interface-elements"></a>Элементы для работы с данными в пользовательском интерфейсе
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Этот раздел содержит информацию обо всех диалоговых окнах и мастерах, используемых вами при проектировании доступа к данным в своих приложениях [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] или Visual C#.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="in-this-section"></a>В этом разделе  
 [Данные смарт-тега](http://msdn.microsoft.com/en-us/1e0a848f-c57b-47ab-b884-eaaa40726f43)  
 Содержит информацию о некоторых командах смарт-тегов, доступных для использования с данными.  
  
 [Добавление набора данных диалогового окна](http://msdn.microsoft.com/en-us/0e03c0ff-212b-4bfa-ac51-3c2adb71ead0)  
 Помещает имеющийся типизированный набор данных или новый нетипизированный набор данных (экземпляр **System.Data.Dataset** класс) в форму или компонент.  
  
 [Advanced SQL диалоговое окно параметров создания](http://msdn.microsoft.com/en-us/41420450-1ff4-4a1a-b85b-6f6901538fef)  
 Позволяет управлять созданием инструкций SQL или хранимых процедур для адаптера данных посредством указания параметров для обновлений, оптимистической блокировки и обновления набора данных.  
  
 [Выберите диалоговое окно экземпляр источника данных](http://msdn.microsoft.com/en-us/51c47f06-fdc5-453e-9178-0a5a2c5c9f34)  
 Позволяет выбрать требуемый набор данных из списка наборов данных в вашем проекте.  
  
 [Выбор источника данных для слияния с диалоговым окном](http://msdn.microsoft.com/en-us/accafff7-f6bd-481c-a121-fe8a76cd681d)  
 Позволяет выбрать источник данных для слияния при наличии нескольких источников данных.  
  
 [Выбор ключа диалоговое окно](http://msdn.microsoft.com/en-us/4ddbfbb7-a80a-412a-b80d-291d86376ca3)  
 Позволяет выбрать ключ, когда столбец принимает участие в многоключевом ограничении.  
  
 [Редакторы коллекций](http://msdn.microsoft.com/library/030095bd-fb9a-4b21-b628-fc1cc5985bb7)  
 Предоставляет ссылки на разделы, посвященные разным редакторам коллекций, позволяющим создавать и изменять отдельные члены коллекции.  
  
 [Нет подключений](http://msdn.microsoft.com/en-us/bb9b2e12-7f76-4ee5-acbb-5d20116ee044)  
 Информирует вас, если набор данных содержит ссылку на строку подключения, не указанную в параметрах приложения.  
  
 [Диалоговое окно ошибки конфигурации данные адаптера](http://msdn.microsoft.com/en-us/9ce65cd2-0c7d-4f51-8685-d68be5f3009b)  
 Отображает одну или несколько ошибок, возникших, когда система Visual Studio пыталась создать экземпляр адаптера данных и задать его свойства.  
  
 [Мастер настройки адаптера данных](http://msdn.microsoft.com/en-us/efff90cb-0e4c-4eb3-87dc-65dd9d418809)  
 Настраивает команды SQL или хранимые процедуры, используемые адаптером данных для считывания данных в набор данных из базы данных и записи их обратно. Этот раздел описывает, как работать с мастером и что делать после окончания такой работы.  
  
 [Диалоговое окно предварительного просмотра адаптера данных](http://msdn.microsoft.com/en-us/1f614cd3-4530-457e-84af-00ccbaea08cc)  
 Позволяет просмотреть, как данные будут заполняться в набор данных адаптером данных. Это удобно, когда требуется проверить, возвращает ли адаптер нужные данные, правильно ли работают сопоставления таблиц, а также определить влияние различных значений параметров.  
  
 [Диалоговое окно входа источника данных](http://msdn.microsoft.com/en-us/6f2d9a57-53c3-4841-bd37-a3643eb68d2e)  
 Позволяет запросить доступ к источнику данных (обычно это база данных), для которого вы еще не прошли аутентификацию.  
  
 [Набор данных вкладке панели элементов](http://msdn.microsoft.com/en-us/fa5f2d6f-924d-4262-ba1b-e9e7f90e7764)  
 Отображает объекты, которые вы можете добавить в типизированный набор данных.  
  
 [Вы хотите включить пароль в строке подключения диалоговое окно](http://msdn.microsoft.com/en-us/193696a7-5213-4396-8328-05ac2df6ee94)  
 Позволяет вам управлять внедрением пароля в строку подключения.  
  
 [Изменение ключа диалоговое окно](http://msdn.microsoft.com/en-us/f5c80e39-3a42-4284-b222-6ca009fd9675)  
 Позволяет определять и изменять ключи.  
  
 [Ограничение внешнего ключа-диалоговое окно](http://msdn.microsoft.com/en-us/45d15629-1f4d-40a7-8708-c9ddfebedc1e)  
 Позволяет установить ограничение внешнего ключа для одного или нескольких столбцов в таблице набора данных, связанной с другой таблицей.  
  
 [Создание набора данных диалоговое окно](http://msdn.microsoft.com/en-us/c0efdbaf-13b1-4ee8-ade6-f8a784126cdc)  
 Позволяет создать новый типизированный набор данных из информации, предоставленной одним или несколькими адаптерами данных, а также добавить таблицы в существующий набор данных.  
  
 [Несколько источников привязки диалоговое окно](http://msdn.microsoft.com/en-us/db76f70c-4fb5-479d-9b64-a67158d48f97)  
 Позволяет выбрать, какой <xref:System.Windows.Forms.BindingSource> необходимо использовать, когда доступно несколько <xref:System.Windows.Forms.BindingSource>.  
  
 [Диалоговое окно предварительного просмотра данных](http://msdn.microsoft.com/en-us/aa4f0d04-2695-4bb8-946d-54a97ae7287f)  
 Позволяет просмотреть данные, возвращаемые запросами в вашем проекте.  
  
 [Диалоговое окно скрипта SQL предварительной версии](http://msdn.microsoft.com/en-us/e9571e8b-821c-492d-9bc8-b44eba898bdd)  
 Отображается как часть [мастер настройки адаптера данных](http://msdn.microsoft.com/en-us/efff90cb-0e4c-4eb3-87dc-65dd9d418809) чтобы можно было просмотреть скрипт SQL, мастер будет использовать для создания хранимых процедур для чтения и записи данных.  
  
 [Диалоговое окно «связи»](http://msdn.microsoft.com/en-us/ab8f4b0e-af4c-4725-a550-e2b2ebe43a02)  
 Позволяет создать отношение ( **DataRelation** объекта), сохраняет сведения о родительских дочерних записях в двух таблицах данных набора данных.  
  
 [Построитель условий поиска-диалоговое окно](http://msdn.microsoft.com/library/0b306b92-f35e-45ef-a4be-3f653cd00c3d)  
 Позволяет создать параметризированный запрос на форме Windows Forms с привязкой к данным и автоматически добавить элементы управления, необходимые для выполнения запроса.  
  
 [Диалоговое окно сопоставления таблицы](http://msdn.microsoft.com/en-us/fb4cec1e-f3c8-4773-b409-c2de15293fea)  
 Позволяет указать, какие столбцы в таблице базы данных или другого источника данных эквивалентны столбцам в таблице набора данных.  
  
 [Ограничение уникальности-диалоговое окно](http://msdn.microsoft.com/en-us/e71a60d7-fae2-4bd0-a1e8-43aae351707d)  
 Позволяет установить уникальное ограничение для одного или нескольких столбцов в таблице нетипизированного набора данных.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Доступ к данным](../data-tools/accessing-data-in-visual-studio.md)  
 Содержит ссылки на разделы, в которых описывается доступ к данным в приложениях Visual Basic и Visual C#.  
  
## <a name="see-also"></a>См. также  
 [Общие сведения о данных приложений в Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Подключение к данным в Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Подготовка приложения для получения данных](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Выборка данных в приложение](../data-tools/fetching-data-into-your-application.md)   
 [Привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Редактирование данных в приложении](../data-tools/editing-data-in-your-application.md)   
 [Проверка данных](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Сохранение данных](../data-tools/saving-data.md)