---
title: Символ поставщика | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- symbol handler
- debugging [Debugging SDK], symbol handler
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f09fbe350afff983bb5fefe880104201441430c3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47562091"
---
# <a name="symbol-provider"></a>Поставщик символов
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [поставщик символов](https://docs.microsoft.com/visualstudio/extensibility/debugger/symbol-provider).  
  
Реализация вычислителя выражений необходимо получить доступ к символической отладочной информации, создаваемой компилятором языка для оценки переменных и выражений. Это достигается путем использования интерфейсы поставщика символов (SP), также вызывается обработчик символов.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] SPs предоставляет для управляемого кода, а также машинного кода, в формате базы данных программы (PDB) символов. При отсутствии надежный, необходимые для вашей программы символов, хранящихся в пользовательском формате, это рекомендуется использовать пакеты обновления, предоставляемые [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="implementation-notes"></a>Примечания по реализации  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Отладчиков ожидать, что дает возможность общаться с SPs, с помощью интерфейсов Common Language Runtime (CLR). Таким образом SP, который будет использоваться механизмы отладки Visual Studio должна поддерживать среды CLR. Полный список всех интерфейсами отладки среды CLR можно найти в debugref.doc, входящий в состав из [!INCLUDE[winsdklong](../../includes/winsdklong-md.md)].  
  
 Если ваш пакет будет работать только с вашего пользовательского модуля отладки, можно реализовать SP по своему усмотрению в зависимости от потребностей вашего модуля отладки.  
  
## <a name="see-also"></a>См. также  
 [Компоненты отладчика](../../extensibility/debugger/debugger-components.md)

