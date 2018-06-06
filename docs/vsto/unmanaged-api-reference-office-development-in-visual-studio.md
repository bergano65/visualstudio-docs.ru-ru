---
title: Справочник по неуправляемым API (Разработка решений Office в Visual Studio)
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, reference
- Office development in Visual Studio, unmanaged API reference
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 97388073d63b25bb17a7f49f4e2c5fb96bf2f572
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2018
ms.locfileid: "34767901"
---
# <a name="unmanaged-api-reference-office-development-in-visual-studio"></a>Справочник по неуправляемым API (Разработка решений Office в Visual Studio)
  Начиная с системы Microsoft Office 2007 приложения Office используют [интерфейс IManagedAddin](../vsto/imanagedaddin-interface.md) интерфейс для вызова надстройки VSTO загрузчика компонента, который входит в состав [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Этот компонент используется для загрузки управляемых надстроек VSTO. Вы можете создать собственный компонент загрузчика надстроек VSTO, реализовав этот интерфейс.  
  
> [!NOTE]  
>  Заинтересованы в разработке решений, расширяющих возможности Office через [нескольких платформ](https://dev.office.com/add-in-availability)? Ознакомьтесь с новой [модель надстроек Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Надстройки Office имеют небольшого размера, по сравнению с надстройками VSTO и решения, и их можно создавать с помощью почти любой технологии веб-программирования, таких как HTML5, JavaScript, CSS3 и XML.  
  
## <a name="in-this-section"></a>Содержание раздела  
 [Интерфейс IManagedAddin](../vsto/imanagedaddin-interface.md)  
 COM-интерфейс, который можно реализовать для загрузки и выгрузки управляемых надстроек VSTO в приложениях Office.  
  
  