---
title: "Символ поставщика | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- symbol handler
- debugging [Debugging SDK], symbol handler
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e0f01e10050fcbdb5cf27390464ae6b8b3e62d64
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="symbol-provider"></a>Символ поставщика
Реализация вычислителя выражений должен получить доступ к символической отладочной информации, создаваемой компилятором языка для вычисления переменных и выражений. Это выполняется путем использования интерфейсов поставщика символ (SP), также называется обработчика символов.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]SPs предоставляет для управляемого кода, а также для машинного кода с помощью формата файла базы данных программы (PDB) символов. При отсутствии надежный, необходимые для вашей программы для использования символов, хранящихся в пользовательском формате, это рекомендуется использовать SPs, предоставляемые [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="implementation-notes"></a>Примечания по реализации  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Ожидать, что отладчики возможность общаться с SPs, с помощью интерфейсов Common Language Runtime (CLR). В результате SP, будет работать отладчики Visual Studio должна поддерживать среды CLR. Полный список всех интерфейсами отладки среды CLR можно найти в debugref.doc, являющейся частью из [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)].  
  
 Если ваш пакет будет работать только с модуль отладки, можно реализовать SP по своему усмотрению, в зависимости от потребностей вашего модуля отладки.  
  
## <a name="see-also"></a>См. также  
 [Компоненты отладчика](../../extensibility/debugger/debugger-components.md)