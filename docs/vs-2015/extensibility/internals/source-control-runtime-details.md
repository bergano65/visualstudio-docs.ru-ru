---
title: Сведения о времени выполнения элемента управления источника | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], runtime details
ms.assetid: 1acd30e0-f98c-4bde-b9cd-4076845887df
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0bb52770557fa37a14040b686dcdfbf345a713a2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68183368"
---
# <a name="source-control-runtime-details"></a>Сведения о среде выполнения системы управления версиями
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Проект добавляется в систему управления версиями, когда пользователь добавляет файл в проект в систему управления версиями или через контроллеров автоматизации, таких как мастер. Проект не содержит для себя что это в системе управления версиями; он поддерживает системы управления версиями, но необходимо добавить к нему вручную.  
  
## <a name="registering-with-a-source-control-package"></a>Регистрация пакета системы управления версиями  
 При добавлении файла в проекте в систему управления версиями, среда вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A> для предоставления четыре непрозрачными строками, которые используются в виде файлов cookie, системы управления версиями. Store эти строки в файле проекта. Эти строки должны быть переданы заглушкой системы управления версиями (Visual Studio компонент, который управляет пакеты системы управления версиями) при запуске проекта типа путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>. Это в свою очередь загружает этот пакет управления соответствующий источник и перенаправляет вызов своей реализации `IVsSccManager2::RegisterSccProject`.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>   
 [Поддержка системы управления версиями](../../extensibility/internals/supporting-source-control.md)
