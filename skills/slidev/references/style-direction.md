---
name: direction
description: Navigation direction-based styling; default typography one step smaller
---

# Navigation Direction Variants

Apply different styles based on navigation direction (forward/backward).

## CSS Classes

```css
/* Delay only when navigating forward */
.slidev-nav-go-forward .slidev-vclick-target {
  transition-delay: 500ms;
}
.slidev-nav-go-backward .slidev-vclick-target {
  transition-delay: 0;
}
```

## UnoCSS Variants

Use `forward:` or `backward:` prefix:

```html
<div v-click class="transition forward:delay-300">Element</div>
```

Animation is only delayed when navigating forward, not when going back.

## Use Case

Create asymmetric animations where entering a slide feels different from leaving it.

---

## Typography: one step smaller by default

Slides are tighter than web pages. For common Markdown structure (`#`–`######`, paragraphs, lists), **default to one semantic size lower** so titles and body copy stay within the canvas.

| Typical web habit | Slidev default |
|-------------------|----------------|
| `#` slide title | `##` unless a single hero title needs `#` |
| `##` section | `###` |
| Plain `p` / long bullets | `text-sm` (and `leading-snug` when dense) |

- **Headings:** Prefer `h2`–`h6` in Markdown where you would use `h1`–`h5` on a marketing page; avoid stacking many `#` levels on one slide.
- **Body:** Short emphasis can stay default size; walls of text use `text-sm` or a compact wrapper class.

```markdown
## Main title (default, not #)

Short hook line.

<ul class="text-sm space-y-1">
  <li>Bullet that would overflow at base size</li>
</ul>
```

### 기본 타이포 (한국어 요약)

- **`h1`~`h6`:** 웹보다 **한 단계 낮은 제목 레벨**을 기본으로 쓴다 (예: 슬라이드 메인 타이틀은 `#` 대신 `##`).
- **`p`, 리스트:** 길어질수록 **`text-sm`** 등으로 **본문도 한 단계 작게** 맞춰 넘침과 과한 위계를 줄인다.
