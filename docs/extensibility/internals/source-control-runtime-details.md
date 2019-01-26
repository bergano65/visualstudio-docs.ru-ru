---
title: Сведения о времени выполнения элемента управления источника | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], runtime details
ms.assetid: 1acd30e0-f98c-4bde-b9cd-4076845887df
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4eae4a8cdea9d98b6c0d8ad173ec4a31fe3ec2f3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55001268"
---
# <a name="source-control-runtime-details"></a>Сведения о среде выполнения системы управления версиями
Проект добавляется в систему управления версиями, когда пользователь добавляет файл в проект в систему управления версиями или через контроллеров автоматизации, таких как мастер. Проект не содержит для себя что это в системе управления версиями; он поддерживает системы управления версиями, но необходимо добавить к нему вручную.  
  
## <a name="registering-with-a-source-control-package"></a>Регистрация пакета системы управления версиями  
 При добавлении файла в проекте в систему управления версиями, среда вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A> для предоставления четыре непрозрачными строками, которые используются в виде файлов cookie, системы управления версиями. Store эти строки в файле проекта. Эти строки должны быть переданы заглушкой системы управления версиями (Visual Studio компонент, который управляет пакеты системы управления версиями) при запуске проекта типа путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>. Это в свою очередь загружает этот пакет управления соответствующий источник и перенаправляет вызов своей реализации `IVsSccManager2::RegisterSccProject`.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>   
 [Поддержка системы управления версиями](../../extensibility/internals/supporting-source-control.md)