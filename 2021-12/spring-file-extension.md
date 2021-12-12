# Spring 프레임워크에서 파일 확장자 가져오는 방법

**코드는 예시입니다!**
```java
package com.spring.kkaemiGG.web.controller;

import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;
import com.spring.kkaemiGG.domain.user.User;
import com.spring.kkaemiGG.service.FileService;
import lombok.RequiredArgsConstructor;
import org.springframework.security.core.annotation.AuthenticationPrincipal;
import org.springframework.web.bind.annotation.PostMapping;
import org.springframework.web.bind.annotation.RequestParam;
import org.springframework.web.multipart.MultipartFile;

@RequiredArgsConstructor
@RequestMapping("/api/v1")
@RestController
public class FileController {

    private final FileService fileService;

    @PostMapping("/images")
    public String uploadImage(
            @RequestParam("image") MultipartFile multipartFile,
            @AuthenticationPrincipal User user
    ) {
        // spring 프레임워크에서 StringUtils를 지원해줌
        // StringUtils안에 getFilenameExtension()이라는 아주 좋은 메소드가 있다.
        String fileExtension = StringUtils.getFilenameExtension(multipartFile.getOriginalFilename());
        return fileService.uploadImage(fileExtension, user);
    }

}
```
