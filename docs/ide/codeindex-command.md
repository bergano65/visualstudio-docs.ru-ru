---
title: Команда CodeIndex
description: Сведения о том, как с помощью команды CodeIndex управлять индексацией кода в Azure DevOps Server (ранее Team Foundation Server).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- command-line tools [Team Foundation Server]
- TFSConfig
- CodeIndex command [Team Foundation Server]
ms.assetid: b79568d4-6a64-4ca9-a1ee-3e57f92a9c5c
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 47875bcece910433a1d20ad66867acd7fdbee8d8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841929"
---
# <a name="codeindex-command"></a>Команда CodeIndex

Команда **CodeIndex** используется для управления индексацией кода на сервере Team Foundation Server. Например, может потребоваться сбросить индекс, чтобы исправить данные CodeLens, или отключить индексацию, чтобы разобраться с проблемами производительности сервера.

## <a name="required-permissions"></a>Необходимые разрешения

Для использования команды **CodeIndex** необходимо являться членом группы безопасности **Администраторы Team Foundation**. См. статью [Разрешения и группы, определенные для Azure DevOps Services и TFS](/azure/devops/organizations/security/permissions?view=vsts&preserve-view=true).

> [!NOTE]
> Для выполнения этой команды необходимо открыть окно командной строки с повышенными привилегиями, даже если вы вошли в систему, используя учетные данные администратора. Также эту команду необходимо выполнять для Team Foundation с уровня приложения.

## <a name="syntax"></a>Синтаксис

```cmd
TFSConfig CodeIndex /indexingStatus | /setIndexing:[ on | off | keepupOnly ] | /ignoreList:[ add | remove | removeAll | view ] ServerPath | /listLargeFiles [/fileCount:FileCount] [/minSize:MinSize] | /reindexAll | /destroyCodeIndex [/noPrompt] | /temporaryDataSizeLimit:[ view | <SizeInGBs> | disable ] | /indexHistoryPeriod:[ view | all | <NumberOfMonths> ] [/collectionName:CollectionName | /collectionId:CollectionId]
```

### <a name="parameters"></a>Параметры

|**Argument**|**Описание**|
|------------------| - |
|`CollectionName`|Задает имя коллекции проектов. Если имя содержит пробелы, заключите его в кавычки, например "веб-сайт компании Fabrikam".|
|`CollectionId`|Задает идентификационный номер коллекции проектов.|
|`ServerPath`|Задает путь к файлу с кодом.|

|**Параметр**|**Описание**|
|----------------| - |
|**/indexingStatus**|Отображает состояние и конфигурацию службы индексации кода.|
|**/setIndexing:**[ on &#124; off &#124; keepupOnly ]|-   **on**: запустить индексацию всех наборов изменений.<br />-   **off**: остановить индексацию всех наборов изменений.<br />-   **keepupOnly**: остановить индексацию созданных ранее наборов изменений и запустить индексацию только новых наборов изменений.|
|**/ignoreList:**[ add &#124; remove &#124; removeAll &#124; view ] `ServerPath`<br /><br /> Можно использовать подстановочный знак (*) в начале, в конце, или на обоих концах серверного пути.|Определяет список файлов исходного кода и путей к ним, которые необходимо исключить из индексирования.<br /><br /> -   **add**: добавить файл, который необходимо исключить из индексации, в список игнорируемых файлов.<br />-   **remove**: удалить файл, который необходимо включить в индексацию, из списка игнорируемых файлов.<br />-   **removeAll**: очистить список игнорируемых файлов и начать индексировать все файлы.<br />-   **view**: просмотреть полный список файлов, которые не будут индексироваться.|
|**/listLargeFiles [/fileCount:** `FileCount` **/minSize:** `MinSize`]|Просмотреть определенное количество файлов, размер которых превышает заданный размер в кБ. Можно воспользоваться параметром **/ignoreList**, чтобы исключить эти файлы из индексации.|
|**/reindexAll**|Очистить ранее индексированные данные и перезапустить индексирование.|
|**/destroyCodeIndex [/noPrompt]**|Удалить индекс кода и все индексированные данные. Не требует подтверждения, если используется параметр **/noPrompt**.|
|**/temporaryDataSizeLimit**:[ view &#124; <`SizeInGBs`> &#124; disable ]|Управляйте количеством временных данных, которые создает CodeLens при обработке наборов изменений. Ограничение по умолчанию составляет 2 ГБ.<br /><br /> -   **view**: отображение текущего ограничения на размер.<br />-   `SizeInGBs`: изменение ограничения на размер.<br />-   **disable**: удаление ограничения на размер.<br /><br /> Проверка этого ограничения выполняется перед тем, как CodeLens обрабатывает новый набор изменений. Если временные данные превышают данное ограничение, то CodeLens приостановит обработку ранних наборов изменений, но не новых. После того как данные будут очищены и их размер станет меньше указанного ограничения, элемент CodeLens перезапустит процесс обработки. Очистка выполняется автоматически раз в день. Это означает, что временные данные могут превысить ограничение перед выполнением очистки.|
|**/indexHistoryPeriod**:[ view &#124; all &#124; <`NumberOfMonths`> ]|Управляйте длительностью индексирования журнала изменений. Это влияет на объем отображаемого журнала CodeLens. Ограничение по умолчанию составляет 12 месяцев. Это означает, что CodeLens показывает журнал изменений только за последние 12 месяцев.<br /><br /> -   **view**: отображение текущего количества месяцев.<br />-   **all**: индексирование всего журнала изменений.<br />-   `NumberOfMonths`: изменение количества месяцев, используемых для индексирования журнала изменений.|
|**/collectionName:** `CollectionName`|Задает имя коллекции проектов, для которой необходимо выполнить команду **CodeIndex**. Является обязательным, если не используется параметр **/CollectionId**.|
|**/collectionId:** `CollectionId`|Задает идентификационный номер коллекции проектов, для которой необходимо выполнить команду **CodeIndex**. Является обязательным, если не используется параметр **/CollectionName**.|

## <a name="examples"></a>Примеры

> [!NOTE]
> Использованные в примерах компании, организации, продукты, доменные имена, адреса электронной почты, логотипы, имена людей, географические названия и события являются вымышленными.  Любые совпадения с реальными именами и названиями случайны.

Просмотр состояния и конфигурации индексации кода:

```cmd
TFSConfig CodeIndex /indexingStatus /collectionName:"Fabrikam Website"
```

Запуск индексации всех наборов изменений:

```cmd
TFSConfig CodeIndex /setIndexing:on /collectionName:"Fabrikam Website"
```

Остановка индексации созданных ранее наборов изменений и запуск индексации только новых наборов изменений:

```cmd
TFSConfig CodeIndex /setIndexing:keepupOnly /collectionName:"Fabrikam Website"
```

Чтобы найти до 50 файлов с размером, превышающим 10 кБ:

```cmd
TFSConfig CodeIndex /listLargeFiles /fileCount:50 /minSize:10 /collectionName:"Fabrikam Website"
```

Исключение определенного файла из индексации и добавление его в список игнорируемых файлов:

```cmd
TFSConfig CodeIndex /ignoreList:add "$/Fabrikam Website/Catalog.cs" /collectionName:"Fabrikam Website"
```

Чтобы просмотреть полный список файлов, которые не будут индексироваться:

```cmd
TFSConfig CodeIndex /ignoreList:view
```

Очистка индексированных данных и перезапуск индексации:

```cmd
TFSConfig CodeIndex /reindexAll /collectionName:"Fabrikam Website"
```

Чтобы сохранить весь журнал набора изменений:

```cmd
TFSConfig CodeIndex /indexHistoryPeriod:all /collectionName:"Fabrikam Website"
```

Чтобы удалить ограничение размера для временных данных элемента CodeLens и продолжения индексации независимо от размера временных данных:

```cmd
TFSConfig CodeIndex /temporaryDataSizeLimit:disable /collectionName:"Fabrikam Website"
```

Удаление индекса кода с подтверждением:

```cmd
TFSConfig CodeIndex /destroyCodeIndex /collectionName:"Fabrikam Website"
```

## <a name="see-also"></a>См. также раздел

- [Поиск изменений кода и других журналов с помощью CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md)
- [Управление конфигурацией сервера с помощью TFSConfig](/azure/devops/server/command-line/tfsconfig-cmd)
