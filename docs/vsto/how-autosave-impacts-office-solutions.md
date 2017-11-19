---
title: "Как эта функция влияет на решения Office | Документы Microsoft"
ms.custom: 
ms.date: 07/20/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: autosave
ms.assetid: b60bb228-0e72-4f24-88bb-397dfc5d50a7
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: 4b4f2b4433395cc03e24273a3eccc04bb31ad30e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="how-autosave-impacts-office-solutions"></a>Как эта функция влияет на решения Office

Эта функция — это функция для Excel, PowerPoint и Word, при включении, включает изменения пользователя сохраняется автоматически и постоянно. Если эта функция отключена, затем сохранить должна запускаться вручную для изменения пользователя, которые необходимо сохранить. С добавлением этой функцией необходимо внести изменения в ваше решение Office для обеспечения работы плавно даже в том случае, когда эта функция включена. Дополнительные сведения см. в разделе [как эта функция затрагивает надстроек и макросов](https://msdn.microsoft.com/vba/office-shared-vba/articles/how-autosave-impacts-addins-and-macros). Дополнительные сведения о автосохранения в целом. в разделе [возможности автосохранения?](https://support.office.com/en-US/article/What-is-AutoSave-6d6bd723-ebfd-4e40-b5f6-ae6e8088f7a5).

Примечание: Эта функция для Windows Desktop Word, Excel и PowerPoint впервые появились в 2017 г. и в настоящее время доступна для подписчиков Office 365. Пользователи, постоянные лицензию для Office 2016 или более ранней версии, не имеют доступ к компоненту соавторства в настоящее время. (Excel Online Excel для Android, Excel для iOS и Excel Mobile в магазине Windows также поддерживают AutoSave). 

## <a name="see-also"></a>См. также
[Разработка решений Office](./developing-office-solutions.md)
