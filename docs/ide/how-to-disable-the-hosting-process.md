---
title: Практическое руководство. Отключение ведущего процесса
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- hosting process, disabling
- vshost.exe, disabling the hosting process
ms.assetid: 9157488d-737f-454b-8d8d-36f99de38bb0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f7970ff97c7aec42f8798da07cf2a4a2b6c8bea8
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31942065"
---
# <a name="how-to-disable-the-hosting-process"></a>Практическое руководство. Отключение ведущего процесса

Включение ведущего процесса может негативно повлиять на вызовы некоторых API. В таких случаях нужно отключить ведущий процесс, чтобы возвратить правильные результаты.

## <a name="to-disable-the-hosting-process"></a>Отключение ведущего процесса

1.  Откройте проект исполняемого файла в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Для проектов, не создающих исполняемые файлы (например, проектов библиотеки классов или службы), этот параметр отсутствует.

2.  В меню **Проект** выберите пункт **Свойства**.

3.  Откройте вкладку **Отладка**.

4.  Снимите флажок **Включить ведущий процесс Visual Studio**.

 Когда ведущий процесс отключен, некоторые функции отладки недоступны или работают хуже. Дополнительные сведения см. в статье [Отладка и ведущий процесс](../debugger/debugging-and-the-hosting-process.md).

 Как правило, отключение ведущего процесса приводит к следующему:

-   Увеличивается время, необходимое для начала отладки [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].

-   Недоступно вычисление выражений во время разработки.

-   Недоступна отладка с частичным доверием.

## <a name="see-also"></a>См. также

- [Debugging and the Hosting Process](../debugger/debugging-and-the-hosting-process.md) (Отладка и ведущий процесс)
- [Ведущий процесс (vshost.exe)](../ide/hosting-process-vshost-exe.md)