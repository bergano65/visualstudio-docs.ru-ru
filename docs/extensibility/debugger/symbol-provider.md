---
title: Поставщик символов Документы Майкрософт
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
ms.openlocfilehash: 31b90846d9494ee046cf9dc4a3e5de9ff033ea3f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712811"
---
# <a name="symbol-provider"></a>Поставщик символов
Реализация оценки выражения должна получить доступ к символической информации об отладке, генерируемой составитером языка, для оценки переменных и выражений. Он делает это, потребляя интерфейсы поставщика символов (SP), также называемого обработчиком символов.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]поставляет SPs для управляемого кода, а также родного кода с использованием формата символа Program DataBase (PDB). Если нет сильной необходимости в использовании в вашей программе символов, хранящихся [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]в пользовательском формате, рекомендуется использовать SPs, поставляемые .

## <a name="implementation-notes"></a>Примечания по реализации
 Двигатели [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отладки ожидают, что они будут взаимодействовать с SPs с помощью интерфейсов Common Language Runtime (CLR). В результате, SP, который будет работать с visual Studio отладки двигателей должны поддерживать CLR. Полный список всех интерфейсов отладки CLR можно найти в debugref.doc, который является частью [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)].

 Если ваш SP будет работать только с пользовательским движком отладки, вы можете реализовать SP, как вы считаете нужным в зависимости от потребностей вашего двигателя отладки.

## <a name="see-also"></a>См. также
- [Компоненты debugger](../../extensibility/debugger/debugger-components.md)
