---
title: Как эта функция влияет на решения Office
ms.custom: ''
ms.date: 07/20/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- autosave
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 21c49599ddc992bf35e6c1464b664a23fb33a691
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/25/2018
ms.locfileid: "34548854"
---
# <a name="how-autosave-impacts-office-solutions"></a>Как эта функция влияет на решения Office

Эта функция — это функция для Excel, PowerPoint и Word, при включении, включает изменения пользователя сохраняется автоматически и постоянно. Если эта функция отключена, затем сохранить должна запускаться вручную для изменения пользователя, которые необходимо сохранить. С добавлением этой функцией необходимо внести изменения в ваше решение Office для обеспечения работы плавно даже в том случае, когда эта функция включена. Дополнительные сведения см. в разделе [как эта функция затрагивает надстроек и макросов](https://msdn.microsoft.com/vba/office-shared-vba/articles/how-autosave-impacts-addins-and-macros). Дополнительные сведения о автосохранения в целом. в разделе [возможности автосохранения?](https://support.office.com/en-US/article/What-is-AutoSave-6d6bd723-ebfd-4e40-b5f6-ae6e8088f7a5).

Примечание: Эта функция для Windows Desktop Word, Excel и PowerPoint впервые появились в 2017 г. и в настоящее время доступна для подписчиков Office 365. Пользователи, которые купили лицензионную для Office 2016 или более ранней версии в настоящее время нет доступа к компоненту соавторства. (Excel Online Excel для Android, Excel для iOS и Excel Mobile в магазине Windows также поддерживают AutoSave). 

## <a name="see-also"></a>См. также
[Разработки решений Office](./developing-office-solutions.md)
