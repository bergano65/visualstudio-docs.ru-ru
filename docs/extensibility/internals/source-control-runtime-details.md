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
ms.openlocfilehash: 3f7501a25596fc0a818277d164337bb0d4e4e077
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56618800"
---
# <a name="source-control-runtime-details"></a>Сведения о среде выполнения системы управления версиями
Проект добавляется в систему управления версиями, когда пользователь добавляет файл в проект в систему управления версиями или через контроллеров автоматизации, таких как мастер. Проект не содержит для себя что это в системе управления версиями; он поддерживает системы управления версиями, но необходимо добавить к нему вручную.

## <a name="registering-with-a-source-control-package"></a>Регистрация пакета системы управления версиями
 При добавлении файла в проекте в систему управления версиями, среда вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A> для предоставления четыре непрозрачными строками, которые используются в виде файлов cookie, системы управления версиями. Store эти строки в файле проекта. Эти строки должны быть переданы заглушкой системы управления версиями (Visual Studio компонент, который управляет пакеты системы управления версиями) при запуске проекта типа путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>. Это в свою очередь загружает этот пакет управления соответствующий источник и перенаправляет вызов своей реализации `IVsSccManager2::RegisterSccProject`.

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>
- [Поддержка системы управления версиями](../../extensibility/internals/supporting-source-control.md)