---
title: Общие метаданные элементов MSBuild | Документация Майкрософт
description: Сведения о необязательных метаданных элементов, которые используются некоторыми пакетами SDK или целевыми объектами MSBuild, но не заданы по умолчанию для каждого элемента.
ms.custom: SEO-VS-2020
ms.date: 07/13/2020
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- msbuild, common item metadata
- item metadata (MSBuild)
ms.assetid: 9857505d-ae15-42f1-936d-6cd7fb9dd276
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 152967fb99442b58d96016e10d8899b57ef35bf6
ms.sourcegitcommit: bd9417123c6ef67aa2215307ba5eeec511e43e02
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/28/2020
ms.locfileid: "92796594"
---
# <a name="common-msbuild-item-metadata"></a>Общие метаданные элементов MSBuild

В следующей таблице описаны необязательные метаданные элементов, которые используются некоторыми пакетами SDK или целевыми объектами MSBuild, но не заданы по умолчанию для каждого элемента. Эти метаданные можно задать, чтобы они влияли на поведение сборки, но только, если используемые пакет SDK или целевые файлы распознают их.

| Метаданные элементов | Пакеты SDK | Описание |
|---------------| ------- | -------------|
|%(Link)| Все |Система проектов Visual Studio использует метаданные `Link` (если они есть) для изменения представления в дереве проекта. Вы можете разместить файл в другой логической структуре папок в **Обозревателе решений**<br />Кроме того, задача `AssignTargetPath` использует `Link`, чтобы определить, куда копировать файл в выходном каталоге (если он является одним из копируемых элементов).|
|%(LinkBase)| Пакет SDK для .NET Core | Позволяет настроить папку, используемую для `Link` метаданных групп элементов. |

## <a name="see-also"></a>См. также

- [Общие свойства проектов MSBuild](../msbuild/common-msbuild-project-properties.md)
- [Общие элементы проектов MSBuild](../msbuild/common-msbuild-project-items.md)
- [Общеизвестные метаданные элементов MSBuild](msbuild-well-known-item-metadata.md)