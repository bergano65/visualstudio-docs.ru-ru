---
title: "Команда CodeIndex | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- command-line tools [Team Foundation Server]
- TFSConfig
- CodeIndex command [Team Foundation Server]
ms.assetid: b79568d4-6a64-4ca9-a1ee-3e57f92a9c5c
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: eaf790d8c02c95047e28ca4d911d7f42a33bbd4f
ms.sourcegitcommit: ebe9fb5eda724936f7a059d35d987c29dffdb50d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/07/2017
---
# <a name="codeindex-command"></a>Команда CodeIndex
Команда **CodeIndex** используется для управления индексацией кода на сервере Team Foundation Server. Например, может потребоваться сбросить индекс, чтобы исправить данные CodeLens, или отключить индексацию, чтобы разобраться с проблемами производительности сервера.  
  
 **Необходимые разрешения**  
  
 Для использования команды **CodeIndex** необходимо являться членом группы безопасности **Администраторы Team Foundation**. См. статью [Permissions and groups defined for Team Services and TFS](https://www.visualstudio.com/docs/setup-admin/permissions) (Разрешения и группы, определенные для Team Services и TFS).  
  
> [!NOTE]
>  Для выполнения этой команды необходимо открыть окно командной строки с повышенными привилегиями, даже если вы вошли в систему, используя учетные данные администратора. Также эту команду необходимо выполнять для Team Foundation с уровня приложения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
TFSConfig CodeIndex /indexingStatus | /setIndexing:[ on | off | keepupOnly ] | /ignoreList:[ add | remove | removeAll | view ] ServerPath | /listLargeFiles [/fileCount:FileCount] [/minSize:MinSize] | /reindexAll | /destroyCodeIndex [/noPrompt] | /temporaryDataSizeLimit:[ view | <SizeInGBs> | disable ] | /indexHistoryPeriod:[ view | all | <NumberOfMonths> ] [/collectionName:CollectionName | /collectionId:CollectionId]  
```  
  
#### <a name="parameters"></a>Параметры  
  
|**Аргумент**|**Описание**|  
|------------------|---------------------|  
|`CollectionName`|Задает имя коллекции командных проектов. Если имя содержит пробелы, заключите его в кавычки, например "веб-сайт компании Fabrikam".|  
|`CollectionId`|Задает идентификационный номер коллекции командных проектов.|  
|`ServerPath`|Задает путь к файлу с кодом.|  
  
|**Параметр**|**Описание**|  
|----------------|---------------------|  
|**/indexingStatus**|Отображает состояние и конфигурацию службы индексации кода.|  
|**/setIndexing:**[ on | off | keepupOnly ]|-   **on**: запустить индексацию всех наборов изменений.<br />-   **off**: остановить индексацию всех наборов изменений.<br />-   **keepupOnly**: остановить индексацию созданных ранее наборов изменений и запустить индексацию только новых наборов изменений.|  
|**/ignoreList:**[ add | remove | removeAll | view ] `ServerPath`<br /><br /> Можно использовать подстановочный знак (*) в начале, в конце, или на обоих концах серверного пути.|Определяет список файлов исходного кода и путей к ним, которые необходимо исключить из индексирования.<br /><br /> -   **add**: добавить файл, который необходимо исключить из индексации, в список игнорируемых файлов.<br />-   **remove**: удалить файл, который необходимо включить в индексацию, из списка игнорируемых файлов.<br />-   **removeAll**: очистить список игнорируемых файлов и начать индексировать все файлы.<br />-   **view**: просмотреть полный список файлов, которые не будут индексироваться.|  
|**/listLargeFiles [/fileCount:** `FileCount` **/minSize:** `MinSize`]|Просмотреть определенное количество файлов, размер которых превышает заданный размер в кБ. Можно воспользоваться параметром **/ignoreList**, чтобы исключить эти файлы из индексации.|  
|**/reindexAll**|Очистить ранее индексированные данные и перезапустить индексирование.|  
|**/destroyCodeIndex [/noPrompt]**|Удалить индекс кода и все индексированные данные. Не требует подтверждения, если используется параметр **/noPrompt**.|  
|**/temporaryDataSizeLimit**:[ view | <`SizeInGBs`> | disable ]|Управляйте количеством временных данных, которые создает CodeLens при обработке наборов изменений. Ограничение по умолчанию составляет 2 ГБ.<br /><br /> -   **view**: отображение текущего ограничения на размер.<br />-   `SizeInGBs`: изменение ограничения на размер.<br />-   **disable**: удаление ограничения на размер.<br /><br /> Проверка этого ограничения выполняется перед тем, как CodeLens обрабатывает новый набор изменений. Если временные данные превышают данное ограничение, то CodeLens приостановит обработку ранних наборов изменений, но не новых. После того как данные будут очищены и их размер станет меньше указанного ограничения, элемент CodeLens перезапустит процесс обработки. Очистка выполняется автоматически раз в день. Это означает, что временные данные могут превысить ограничение перед выполнением очистки.|  
|**/indexHistoryPeriod**:[ view | all | <`NumberOfMonths`> ]|Управляйте длительностью индексирования журнала изменений. Это влияет на объем отображаемого журнала CodeLens. Ограничение по умолчанию составляет 12 месяцев. Это означает, что CodeLens показывает журнал изменений только за последние 12 месяцев.<br /><br /> -   **view**: отображение текущего количества месяцев.<br />-   **all**: индексирование всего журнала изменений.<br />-   `NumberOfMonths`: изменение количества месяцев, используемых для индексирования журнала изменений.|  
|**/collectionName:** `CollectionName`|задает имя коллекции командных проектов, для которой необходимо выполнить команду **CodeIndex**. Является обязательным, если не используется параметр **/CollectionId**.|  
|**/collectionId:** `CollectionId`|задает идентификационный номер коллекции командных проектов, для которой необходимо выполнить команду **CodeIndex**. Является обязательным, если не используется параметр **/CollectionName**.|  
  
## <a name="examples"></a>Примеры  
  
> [!NOTE]
>  Использованные в примерах компании, организации, продукты, доменные имена, адреса электронной почты, логотипы, имена людей, географические названия и события являются вымышленными.  Любые совпадения с реальными именами и названиями случайны.  
  
 Просмотр состояния и конфигурации индексации кода:  
  
```  
TFSConfig CodeIndex /indexingStatus /collectionName:"Fabrikam Web Site"  
```  
  
 Запуск индексации всех наборов изменений:  
  
```  
TFSConfig CodeIndex /setIndexing:on /collectionName:"Fabrikam Web Site"  
```  
  
 Остановка индексации созданных ранее наборов изменений и запуск индексации только новых наборов изменений:  
  
```  
TFSConfig CodeIndex /setIndexing:keepupOnly /collectionName:"Fabrikam Web Site"  
```  
  
 Чтобы найти до 50 файлов с размером, превышающим 10 кБ:  
  
```  
TFSConfig CodeIndex /listLargeFiles /fileCount:50 /minSize:10 /collectionName:"Fabrikam Web Site"  
```  
  
 Исключение определенного файла из индексации и добавление его в список игнорируемых файлов:  
  
```  
TFSConfig CodeIndex /ignoreList:add "$/Fabrikam Web Site/Catalog.cs" /collectionName:"Fabrikam Web Site"  
```  
  
 Чтобы просмотреть полный список файлов, которые не будут индексироваться:  
  
```  
TFSConfig CodeIndex /ignoreList:view  
```  
  
 Очистка индексированных данных и перезапуск индексации:  
  
```  
TFSConfig CodeIndex /reindexAll /collectionName:"Fabrikam Web Site"  
```  
  
 Чтобы сохранить весь журнал набора изменений:  
  
```  
TFSConfig CodeIndex /indexHistoryPeriod:all /collectionName:"Fabrikam Web Site"  
```  
  
 Чтобы удалить ограничение размера для временных данных элемента CodeLens и продолжения индексации независимо от размера временных данных:  
  
```  
TFSConfig CodeIndex /temporaryDataSizeLimit:disable /collectionName:"Fabrikam Web Site"  
```  
  
 Удаление индекса кода с подтверждением:  
  
```  
TFSConfig CodeIndex /destroyCodeIndex /collectionName:"Fabrikam Web Site"  
```  
  
## <a name="see-also"></a>См. также

[Поиск изменений кода и других журналов с помощью CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md)  
[Управление конфигурацией сервера с помощью TFSConfig](http://msdn.microsoft.com/en-us/94424190-3b6b-4f33-a6b6-5807f4225b62)  
[Средства командной строки для TFS](http://msdn.microsoft.com/en-us/be8c997a-b97b-4e59-97f5-04db0a601a6c)