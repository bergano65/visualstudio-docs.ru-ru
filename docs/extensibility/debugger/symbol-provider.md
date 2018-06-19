---
title: Символ поставщика | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- symbol handler
- debugging [Debugging SDK], symbol handler
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a98a5b80126bcb11109acedc2d24f226cde3714a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31126178"
---
# <a name="symbol-provider"></a>Символ поставщика
Реализация вычислителя выражений должен получить доступ к символической отладочной информации, создаваемой компилятором языка для вычисления переменных и выражений. Это выполняется путем использования интерфейсов поставщика символ (SP), также называется обработчика символов.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] SPs предоставляет для управляемого кода, а также для машинного кода с помощью формата файла базы данных программы (PDB) символов. При отсутствии надежный, необходимые для вашей программы для использования символов, хранящихся в пользовательском формате, это рекомендуется использовать SPs, предоставляемые [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="implementation-notes"></a>Примечания по реализации  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Ожидать, что отладчики возможность общаться с SPs, с помощью интерфейсов Common Language Runtime (CLR). В результате SP, будет работать отладчики Visual Studio должна поддерживать среды CLR. Полный список всех интерфейсами отладки среды CLR можно найти в debugref.doc, являющейся частью из [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)].  
  
 Если ваш пакет будет работать только с модуль отладки, можно реализовать SP по своему усмотрению, в зависимости от потребностей вашего модуля отладки.  
  
## <a name="see-also"></a>См. также  
 [Компоненты отладчика](../../extensibility/debugger/debugger-components.md)