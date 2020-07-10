# sympathy-backend library

## Image util

### Function: ScaleImage
``` 
func ScaleImage(i image.Image, w, h int) (image.Image, error) 
```
- **Usage:** To scale an image to specified width and height

- **Input param:**

  - i: Image need to scale width and height

  - w: output width

  - h: output height


### Function: EncodeImage
```
func EncodeImage(buf io.Writer, i image.Image, ext string) error
```
- **Usage:** Write the image i to buf in jpeg, png or gif format

- **Input param:**

  - buf: writer

  - i: image need to encode

  - ext: extension of input image


### Function: GetImageByPath
```
func GetImageByPath(path string) (draw.Image, string)
```
- **Usage:** Get the image from specified path

- **Input param:**

  - path: path of image need to get


### Function: GetImageByPathWithRect
```
func GetImageByPathWithRect(path string, rect image.Rectangle) (draw.Image, string)
```
- **Usage:** Get the image from specified path and rectangle

- **Input param:**

  - path: path of image need to get

  - rect: rectangle of image
<br>

---
## Pagination

### Function: CreatePager
```
type (
	// Pager ...
	Pager struct {
		TotalCount  int64
		PerPage     int64
		CurrentPage int64
		PrevItem    PageItem
		NextItem    PageItem
		PageLinks   []PageItem
	}

	// PageItem ...
	PageItem struct {
		Page       int64
		Label      string
		Location   string
		IsDisabled bool
		IsCurrent  bool
	}
)
```

<br>

```
func CreatePager(ctx context.Context, count, perpage, current int64) (*Pager, error)
```
- **Usage:** Create a pagination pager

- **Input param:**

  - ctx: a context

  - count: total result

  - perpage: number result per page

  - current: current page


### Function: getLocation
```
func getLocation(location string, page int64) string
```
- **Usage:** Get location (url) of specified page

- **Input param:**

  - location: current location

  - page: specified page need to get location

<br>

---
## Param Ulti

### Function: paramTo
```
func paramTo(kind reflect.Kind, param string) (interface{}, bool, error)
```
- **Usage:** Convert params to a specified type

- **Input param:**

  - kind: type need to convert to

  - param: a URL param


### Function: ParamToInt64
```
func ParamToInt64(param string) (int64, bool, error)
```
- **Usage:** Convert params to type int64

- **Input param:**

  - param: a URL param


### Function: ParamToStr
```
func ParamToStr(param string) (string, bool, error)
```
- **Usage:** Convert params to type string

- **Input param:**

  - param: a URL param

<br>

---
## Ultility

### Function: Random
```
func Random(n int) string
```
- **Usage:** Make a random string with n characters both uppercase and lowercase

- **Input param:**

  - n: number of characters


### Function: RandomLC
```
func RandomLC(n int) string
```
- **Usage:** Make a random string with n lowercase characters

- **Input param:**

  - n: number of characters


### Function: GetHash256
```
func GetHash256(str string) string
```
- **Usage:** Encrypt a string using SHA-256 algorithm

- **Input param:**

  - str: string


### Function: PasswordHash
```
func PasswordHash(pw string) (string, error)
```
- **Usage:** Generate a hash password from password

- **Input param:**

  - pw: password


### Function: PasswordVerify
```
func PasswordVerify(hash, pw string) error
```
- **Usage:** Compare password with hash password to verify

- **Input param:**

  - hash: hash password

  - pw: password
