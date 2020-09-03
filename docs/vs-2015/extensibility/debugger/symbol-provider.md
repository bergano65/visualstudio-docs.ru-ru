---
title: Поставщик символов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- symbol handler
- debugging [Debugging SDK], symbol handler
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6af1af9d2e178241fa8a5957e18c1a5333fa4b09
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68178890"
---
# <a name="symbol-provider"></a>Поставщик символов
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Реализация средства оценки выражений должна получить доступ к символьной отладочной информации, созданной компилятором языка, для оценки переменных и выражений. Это достигается за счет использования интерфейсов поставщика символов (SP), также называемого обработчиком символов.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] предоставляет SPs для управляемого кода и машинного кода, используя формат файла символов базы данных программы (PDB). Если программа не должна использовать символы, хранящиеся в пользовательском формате, рекомендуется использовать SPs, предоставляемые [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
## <a name="implementation-notes"></a>Примечания по реализации  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Модули отладки должны взаимодействовать с SPs с помощью интерфейсов CLR. В результате пакет обновления, который будет работать с механизмами отладки Visual Studio, должен поддерживать среду CLR. Полный список всех интерфейсов отладки среды CLR можно найти в debugref.doc, который является частью компонента [!INCLUDE[winsdklong](../../includes/winsdklong-md.md)] .  
  
 Если ваш пакет обновления будет работать только с пользовательским модулем отладки, вы можете реализовать его так, как вы видите, в зависимости от потребностей модуля отладки.  
  
## <a name="see-also"></a>См. также:  
 [Компоненты отладчика](../../extensibility/debugger/debugger-components.md)
