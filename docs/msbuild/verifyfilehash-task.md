---
title: Задача VerifyFileHash | Документация Майкрософт
ms.date: 01/28/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- VerifyFileHash task [MSBuild]
- MSBuild, VerifyFileHash task
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: faf7738019680085020b9650094931d5860bc29b
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56618384"
---
# <a name="verifyfilehash-task"></a>Задача VerifyFileHash

Проверяет, что файл соответствует ожидаемому хэшу файла.

Эта задача была добавлена в версии 15.8, но требует [обходное решение](https://github.com/Microsoft/msbuild/pull/3999#issuecomment-458193272) для версий MSBuild до 16.0.

## <a name="task-parameters"></a>Параметры задачи

 В следующей таблице приводятся параметры задачи `VerifyFileHash` .

|Параметр|Описание|
|---------------|-----------------|
|`File`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem> .<br /><br />Файлы, которые требуется хэшировать и проверить.|
|`Hash`|Обязательный параметр `String` .<br /><br />Ожидаемый хэш файла.|
|`Items`|Выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br />Входные данные `Files` с дополнительными метаданными, заданные для хэша файла.|
|`Algorithm`|Необязательный параметр `String` .<br /><br />Алгоритм. Допустимые значения: `SHA256`, `SHA384`, `SHA512`. По умолчанию = `SHA256`.|
|`HashEncoding`|Необязательный параметр `String` .<br /><br />Кодировка, используемая для созданных хэшей. По умолчанию — `hex`. Допустимые значения = `hex`, `base64`.|

## <a name="example"></a>Пример

В следующем примере задача `VerifyFileHash` проверяет свою контрольную сумму.

```xml
<Project>
  <Target Name="VerifyHash">
    <GetFileHash Files="$(MSBuildProjectFullPath)">
      <Output
          TaskParameter="Items"
          ItemName="FilesWithHashes" />
    </GetFileHash>

    <Message Importance="High"
             Text="@(FilesWithHashes->'%(Identity): %(FileHash)')" />

    <VerifyFileHash File="$(MSBuildThisFileFullPath)"
                    Hash="$(ExpectedHash)" />
  </Target>
</Project>
```

## <a name="see-also"></a>См. также

- [Задачи](../msbuild/msbuild-tasks.md)
- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)