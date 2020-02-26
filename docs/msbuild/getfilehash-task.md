---
title: Задача GetFileHash | Документация Майкрософт
ms.date: 01/28/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- GetFileHash task [MSBuild]
- MSBuild, GetFileHash task
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a8f3de9a4f2fe848e1cbd41e14e82498845ca2cf
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/25/2020
ms.locfileid: "77578660"
---
# <a name="getfilehash-task"></a>Задача GetFileHash

Вычисляет контрольные суммы содержимого файла или набора файлов.

Эта задача была добавлена в версии 15.8, но требует [обходное решение](https://github.com/Microsoft/msbuild/pull/3999#issuecomment-458193272) для версий MSBuild до 16.0.

## <a name="task-parameters"></a>Параметры задачи

 В следующей таблице приводятся параметры задачи `GetFileHash` .

|Параметр|Описание|
|---------------|-----------------|
|`Files`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br />Файлы, которые нужно хэшировать.|
|`Items`|Выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br />Входные данные `Files` с дополнительными метаданными, заданные для хэша файла.|
|`Hash`|Выходной параметр `String`.<br /><br />Хэш файла. Эти выходные данные задаются только в том случае, если передан только один элемент.|
|`Algorithm`|Необязательный параметр `String`.<br /><br />Алгоритм. Допустимые значения: `SHA256`, `SHA384`, `SHA512`. По умолчанию = `SHA256`.|
|`MetadataName`|Необязательный параметр `String`.<br /><br />Имя метаданных, где хранится хэш в каждом элементе. По умолчанию — `FileHash`.|
|`HashEncoding`|Необязательный параметр `String`.<br /><br />Кодировка, используемая для созданных хэшей. По умолчанию — `hex`. Допустимые значения = `hex`, `base64`.|

## <a name="example"></a>Пример

В следующем примере используется задача `GetFileHash` для определения и вывода контрольной суммы элементов `FilesToHash`.

```xml
<Project>
  <ItemGroup>
    <FilesToHash Include="$(MSBuildThisFileDirectory)\*" />
  </ItemGroup>
  <Target Name="GetHash">
    <GetFileHash Files="@(FilesToHash)">
      <Output
          TaskParameter="Items"
          ItemName="FilesWithHashes" />
    </GetFileHash>

    <Message Importance="High"
             Text="@(FilesWithHashes->'%(Identity): %(FileHash)')" />
  </Target>
</Project>
```

## <a name="see-also"></a>См. также

- [Задачи](../msbuild/msbuild-tasks.md)

- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)