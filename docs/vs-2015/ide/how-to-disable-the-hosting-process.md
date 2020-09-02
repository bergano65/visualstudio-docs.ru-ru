---
title: Практическое руководство. Отключение ведущего процесса | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- hosting process, disabling
- vshost.exe, disabling the hosting process
ms.assetid: 9157488d-737f-454b-8d8d-36f99de38bb0
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 95dcd7da113bfe996d00e617b7c8e2f9b68864d7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667976"
---
# <a name="how-to-disable-the-hosting-process"></a>How to: Disable the Hosting Process
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Включение ведущего процесса может негативно повлиять на вызовы некоторых API. В таких случаях нужно отключить ведущий процесс, чтобы возвратить правильные результаты.

### <a name="to-disable-the-hosting-process"></a>Отключение ведущего процесса

1. Откройте проект исполняемого файла в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Для проектов, не создающих исполняемые файлы (например, проектов библиотеки классов или службы), этот параметр отсутствует.

2. В меню **Проект** выберите **Свойства**.

3. Откройте вкладку **Отладка**.

4. Снимите флажок **Включить ведущий процесс Visual Studio**.

   Когда ведущий процесс отключен, некоторые функции отладки недоступны или работают хуже. Дополнительные сведения см. [в разделе Отладка и ведущий процесс](../debugger/debugging-and-the-hosting-process.md).

   Как правило, отключение ведущего процесса приводит к следующему:

- Увеличивается время, необходимое для начала отладки [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].

- Недоступно вычисление выражений во время разработки.

- Недоступна отладка с частичным доверием.

## <a name="see-also"></a>См. также:
 [Отладка и](../debugger/debugging-and-the-hosting-process.md) ведущий процесс размещения процесса [(vshost.exe)](../ide/hosting-process-vshost-exe.md) [строятся во время разработки приложения](https://msdn.microsoft.com/c9497d62-3b7b-4449-88e8-cf27acc9efe6)
