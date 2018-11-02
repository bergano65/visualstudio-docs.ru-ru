---
title: CATID для объектов, которые обычно используются для расширения проектов | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, CATIDs
- GUIDs, VSPackages
- CATIDs for VSPackages
ms.assetid: 0c7fdb66-ed96-4b36-89f6-021bca573572
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c4d3bc6ce2732ef2b360d083d207bef5b2666b2f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49861141"
---
# <a name="catids-for-objects-that-are-typically-used-to-extend-projects"></a>CATID для объектов, которые обычно используются для расширения проектов
В следующей таблице перечислены идентификаторы CATID, которые используются для расширения `Project` и `ProjectItem` объектов автоматизации для [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], и [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] проектов. Эти идентификаторы CATID определяются в *VSLangProj.olb*.  

## <a name="listing-of-catids"></a>Список CATID  

|name|Идентификатор GUID|  
|----------|----------|  
|<xref:VSLangProj.PrjCATID.prjCATIDProject>|{610D4614-D0D5-11D2-8599-006097C68E81}|  
|<xref:VSLangProj.PrjCATID.prjCATIDProjectItem>|{610D4615-D0D5-11D2-8599-006097C68E81}|  

## <a name="visual-basic-catids"></a>CATID Visual Basic  
 В следующей таблице перечислены идентификаторы CATID, которые используются для расширения [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] просматривать объекты. Все они определены в *VSLangProj.olb*.  

|name|Идентификатор GUID|  
|----------|----------|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBProjectBrowseObject>|{E0FDC879-C32A-4751-A3D3-0B3824BD575F}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBProjectConfigBrowseObject>|{67F8DD11-14EB-489b-87F0-F01C52AF3870}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBFileBrowseObject>|{EA5BD05D-3C72-40A5-95A0-28A2773311CA}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBFolderBrowseObject>|{932DC619-2EAA-4192-B7E6-3D15AD31DF49}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBReferenceBrowseObject>|{2289B812-8191-4e81-B7B3-174045AB0CB5}|  

## <a name="visual-c-catids"></a>CATID Visual C#  
 Следующие идентификаторы CATID можно использовать для расширения [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] просматривать объекты. Все они определены в *VSLangProj.olb*.  

|name|Идентификатор GUID|  
|----------|----------|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpProjectBrowseObject>|{4EF9F003-DE95-4d60-96B0-212979F2A857}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpProjectConfigBrowseObject>|{A12CE10A-227F-4963-ADB6-3A43388513CA}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpFileBrowseObject>|{8D58E6AF-ED4E-48B0-8C7B-C74EF0735451}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpFolderBrowseObject>|{914FE278-054A-45DB-BF9E-5F22484CC84C}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpReferenceBrowseObject>|{2F0FA3B8-C855-4a4e-95A5-CB45C67D6C27}|  

## <a name="c-catids"></a>CATID для C++  
 Следующие [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] CATID недоступны в библиотеках типов в системе проектов [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .NET 2003 и должны быть включены в коде, каждый раз, когда вы хотите расширить эти объекты проекта. Эти идентификаторы CATID будут включены в библиотеки типов в более поздних версиях [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  

|name|Идентификатор GUID|  
|----------|----------|  
|`CVCProjectNode`|{EE8299CB-19B6-4f20-ABEA-E1FD9A33B683}|  
|`CVCFolderNode`|{EE8299CA-19B6-4f20-ABEA-E1FD9A33B683}|  
|`CVCFileNode`|{EE8299C9-19B6-4f20-ABEA-E1FD9A33B683}|  

 В следующем примере кода показано, как программировать эти идентификаторы CATID в коде.  

```  
const LPOLESTR CVCProjectNode::s_wszCATID = L"{EE8299CB-19B6-4f20-ABEA-E1FD9A33B683}";  
const LPOLESTR CVCFolderNode::s_wszCATID = L"{EE8299CA-19B6-4f20-ABEA-E1FD9A33B683}";  
const LPOLESTR CVCFileNode::s_wszCATID = L"{EE8299C9-19B6-4f20-ABEA-E1FD9A33B683}";  
```  

 Следующие [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] CATID также не предоставляются в библиотеки типов в системе проектов [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .NET 2003 и должны быть включены в коде, каждый раз, когда вы хотите расширить эти объекты проекта. Эти идентификаторы CATID доступны только в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .NET 2003 и не будут доступны в более поздних версиях [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  

|name|Идентификатор GUID|  
|----------|----------|  
|`CVCAssemblyReferenceNode`|{FE8299C9-19B6-4f20-ABEA-E1FD9A33B683}|  
|`CVCProjectReferenceNode`|{593DCFCE-20A7-48e4-ACA1-49ADE9049887}|  
|`CVCActiveXReferenceNode`|{9E8182D3-C60A-44f4-A74B-14C90EF9CACE}|  
|`CVCReferences`|{FE8299CA-19B6-4f20-ABEA-E1FD9A33B683}|  

 В следующем примере кода показано, как программировать эти идентификаторы CATID в коде:  

```  
const LPOLESTR CVCAssemblyReferenceNode::s_wszCATID = L"{FE8299C9-19B6-4f20-ABEA-E1FD9A33B683}";  
const LPOLESTR CVCProjectReferenceNode::s_wszCATID = L"{593DCFCE-20A7-48e4-ACA1-49ADE9049887}";  
const LPOLESTR CVCActiveXReferenceNode::s_wszCATID = L"{9E8182D3-C60A-44f4-A74B-14C90EF9CACE}";  
const LPOLESTR CVCReferences::s_wszCATID = L"{FE8299CA-19B6-4f20-ABEA-E1FD9A33B683}";  
```  

 Идентификаторы GUID для [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] и [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] в следующей таблице показаны типы проектов.  


| Тип проекта | Идентификатор GUID |
| - | - |
| [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] | {FAE04EC0-301F-11D3-BF4B-00C04F79EFBC} |
| [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] | {F184B08F-C81C-45F6-A57F-5ABD9991F28F} |

## <a name="see-also"></a>См. также  
 [Добавьте в проект и шаблоны элементов проекта](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Регистрация шаблонов проектов и элементов](../../extensibility/internals/registering-project-and-item-templates.md)