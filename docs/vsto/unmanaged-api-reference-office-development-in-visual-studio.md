---
title: Справочник по неуправляемым API (Разработка решений Office в Visual Studio)
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, reference
- Office development in Visual Studio, unmanaged API reference
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f61f764028959cce4015834c53d6ca74bde46bed
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2019
ms.locfileid: "54863547"
---
# <a name="unmanaged-api-reference-office-development-in-visual-studio"></a>Справочник по неуправляемым API (Разработка решений Office в Visual Studio)
  Начиная с выпуска 2007 системы Microsoft Office, приложения Office используют [интерфейс IManagedAddin](../vsto/imanagedaddin-interface.md) интерфейс для вызова надстройки VSTO загрузчика компонентом, который входит в состав [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Этот компонент используется для загрузки управляемых надстроек VSTO. Вы можете создать собственный компонент загрузчика надстроек VSTO, реализовав этот интерфейс.  
  
> [!NOTE]  
>  Занимаетесь разработкой решений, расширяющих возможности Office по [нескольких платформ](https://dev.office.com/add-in-availability)? Ознакомьтесь с новой [модель надстроек Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Надстройки Office имеют небольшого размера, по сравнению с надстройками VSTO и решения, и вы можете создавать их с помощью почти любой технологии веб-программирования, таких как HTML5, JavaScript, CSS3 и XML.  
  
## <a name="in-this-section"></a>Содержание раздела  
 [Интерфейс IManagedAddin](../vsto/imanagedaddin-interface.md)  
 COM-интерфейс, который можно реализовать для загрузки и выгрузки управляемых надстроек VSTO в приложениях Office.  
