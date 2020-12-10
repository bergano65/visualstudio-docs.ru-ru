---
title: Поставщик символов | Документация Майкрософт
description: Узнайте о поставщиках символов, предоставляемых Visual Studio, чтобы позволить Вычислителю выражений оценивать переменные и выражения.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- symbol handler
- debugging [Debugging SDK], symbol handler
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 043014ebababd990c9cae03f28cb1b642d576071
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996049"
---
# <a name="symbol-provider"></a>Поставщик символов
Реализация средства оценки выражений должна получить доступ к символьной отладочной информации, созданной компилятором языка, для оценки переменных и выражений. Это достигается за счет использования интерфейсов поставщика символов (SP), также называемого обработчиком символов.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] предоставляет SPs для управляемого кода и машинного кода, используя формат файла символов базы данных программы (PDB). Если программа не должна использовать символы, хранящиеся в пользовательском формате, рекомендуется использовать SPs, предоставляемые [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="implementation-notes"></a>Примечания по реализации
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Модули отладки должны взаимодействовать с SPs с помощью интерфейсов CLR. В результате пакет обновления, который будет работать с механизмами отладки Visual Studio, должен поддерживать среду CLR. Полный список всех интерфейсов отладки среды CLR можно найти в debugref.doc, который является частью компонента [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)] .

 Если ваш пакет обновления будет работать только с пользовательским модулем отладки, вы можете реализовать его так, как вы видите, в зависимости от потребностей модуля отладки.

## <a name="see-also"></a>См. также раздел
- [Компоненты отладчика](../../extensibility/debugger/debugger-components.md)
