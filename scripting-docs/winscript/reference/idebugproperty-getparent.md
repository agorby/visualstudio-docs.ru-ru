---
title: "IDebugProperty::GetParent | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugProperty.GetParent
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugProperty::GetParent
ms.assetid: 673d625b-acca-45c4-88f4-b72275042f8f
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8559f7c7d5baa5144449f67850d2fe882c379e94
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="idebugpropertygetparent"></a>IDebugProperty::GetParent
Возвращает свойство родительского свойства.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetParent (  
   IDebugProperty** ppParent  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppParent`  
 [out] Возвращает `IDebugProperty` интерфейс, который представляет родительский объект свойства.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает допустимую `HRESULT`, обычно `S_OK`.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugProperty](../../winscript/reference/idebugproperty-interface.md)