---
title: Справочник по API (Разработка решений Office в Visual Studio) неуправляемого | Документы Microsoft
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
ms.openlocfilehash: e06ec998dc4b9c23b38526563ce8b501866769b0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="unmanaged-api-reference-office-development-in-visual-studio"></a>Справочные материалы по неуправляемым API (разработка решений Office в Visual Studio)
  Начиная с системы Microsoft Office 2007 приложения Office используют [интерфейс IManagedAddin](../vsto/imanagedaddin-interface.md) интерфейс для вызова надстройки VSTO загрузчика компонента, который входит в состав [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Этот компонент используется для загрузки управляемых надстроек VSTO. Вы можете создать собственный компонент загрузчика надстроек VSTO, реализовав этот интерфейс.  
  
> [!NOTE]  
>  Заинтересованы в разработке решений, расширяющих возможности Office через [нескольких платформ](https://dev.office.com/add-in-availability)? Ознакомьтесь с новой [модель надстроек Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Надстройки Office имеют небольшого размера, по сравнению с надстройками VSTO и решения, и их можно создавать с помощью почти любой технологии веб-программирования, таких как HTML5, JavaScript, CSS3 и XML.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Интерфейс IManagedAddin](../vsto/imanagedaddin-interface.md)  
 COM-интерфейс, который можно реализовать для загрузки и выгрузки управляемых надстроек VSTO в приложениях Office.  
  
  