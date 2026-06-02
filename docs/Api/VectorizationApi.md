# VectorizerAI\VectorizationApi

All URIs are relative to https://api.vectorizer.ai/api/v1, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**postDelete()**](VectorizationApi.md#postDelete) | **POST** /delete | Delete a retained image |
| [**postDownload()**](VectorizationApi.md#postDownload) | **POST** /download | Download a retained result |
| [**postVectorize()**](VectorizationApi.md#postVectorize) | **POST** /vectorize | Vectorize an image |


## `postDelete()`

```php
postDelete($image_token): \VectorizerAI\Model\DeleteImageResponse
```

Delete a retained image

Delete a retained image and result before its retention period expires.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = VectorizerAI\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new VectorizerAI\Api\VectorizationApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

$associative_array = [
    'image_token' => 'image_token_example', // string | Image Token to delete before its retention period expires.
];

try {
    $result = $apiInstance->postDelete($associate_array);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling VectorizationApi->postDelete: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

Note: the input parameter is an associative array with the keys listed as the parameter names below.

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **image_token** | **string**| Image Token to delete before its retention period expires. | |

### Return type

[**\VectorizerAI\Model\DeleteImageResponse**](../Model/DeleteImageResponse.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `multipart/form-data`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `postDownload()`

```php
postDownload($image_token, $receipt, $output_file_format, $output_shape_stacking, $output_group_by, $output_draw_style, $output_strokes_stroke_width, $output_strokes_non_scaling_stroke, $output_strokes_use_override_color, $output_strokes_override_color, $output_gap_filler_enabled, $output_gap_filler_non_scaling_stroke, $output_gap_filler_clip, $output_gap_filler_stroke_width, $output_parameterized_shapes_flatten, $output_curves_line_fit_tolerance, $output_curves_allowed_quadratic_bezier, $output_curves_allowed_cubic_bezier, $output_curves_allowed_circular_arc, $output_curves_allowed_elliptical_arc, $output_svg_version, $output_svg_fixed_size, $output_svg_adobe_compatibility_mode, $output_pdf_version, $output_pdf_compression_mode, $output_eps_version, $output_dxf_compatibility_level, $output_bitmap_anti_aliasing_mode, $output_size_scale, $output_size_width, $output_size_height, $output_size_unit, $output_size_aspect_ratio, $output_size_align_x, $output_size_align_y, $output_size_input_dpi, $output_size_output_dpi): \SplFileObject
```

Download a retained result

Download a production result from a retained Image Token, optionally changing output.file_format and other output options. Include receipt when downloading additional formats after upgrading a preview result.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = VectorizerAI\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new VectorizerAI\Api\VectorizationApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

$associative_array = [
    'image_token' => 'image_token_example', // string | Image Token returned from a vectorize request with policy.retention_days > 0.
    'receipt' => 'receipt_example', // string | Receipt returned in the X-Receipt response header when upgrading a preview result to production. Include it when downloading additional formats from that upgraded preview.
    'output_file_format' => 'svg', // string | Output file format to generate.
    'output_shape_stacking' => 'cutouts', // string | Whether shapes are cut out of each other or stacked atop each other.
    'output_group_by' => 'none', // string | Grouping of shapes in output.
    'output_draw_style' => 'fill_shapes', // string | How shapes are rendered.
    'output_strokes_stroke_width' => 1, // float | Width of stroke for shape outlines (when enabled).
    'output_strokes_non_scaling_stroke' => true, // bool | Use non-scaling strokes when drawing shape outlines.
    'output_strokes_use_override_color' => false, // bool | Override shape color with a specific color.
    'output_strokes_override_color' => '#000000', // string | Color value to override shape stroke color if enabled. Must be in '#RRGGBB' or 'rgba(r,g,b,a)' format.
    'output_gap_filler_enabled' => true, // bool | Enable filling small visual gaps caused by vector rendering artifacts.
    'output_gap_filler_non_scaling_stroke' => true, // bool | Use non-scaling strokes for gap filling.
    'output_gap_filler_clip' => false, // bool | Clip gap filler strokes to shape bounds when stacking shapes.
    'output_gap_filler_stroke_width' => 2, // float | Width of the gap filler strokes (in output units).
    'output_parameterized_shapes_flatten' => false, // bool | Whether to flatten detected circles, rectangles, and stars to curves.
    'output_curves_line_fit_tolerance' => 0.1, // float | Maximum allowed error when approximating curves with line segments.
    'output_curves_allowed_quadratic_bezier' => true, // bool | Allow quadratic Bézier curves in the output.
    'output_curves_allowed_cubic_bezier' => true, // bool | Allow cubic Bézier curves in the output.
    'output_curves_allowed_circular_arc' => true, // bool | Allow circular arcs in the output.
    'output_curves_allowed_elliptical_arc' => true, // bool | Allow elliptical arcs in the output.
    'output_svg_version' => 'svg_1_1', // string | SVG version to declare in the SVG output.
    'output_svg_fixed_size' => false, // bool | Whether to fix the SVG dimensions in the output file.
    'output_svg_adobe_compatibility_mode' => false, // bool | Enable Illustrator compatibility by disabling unsupported SVG features.
    'output_pdf_version' => 'PDF_1_4', // string | PDF version to generate for PDF output.
    'output_pdf_compression_mode' => 'Deflate', // string | Compression method to apply to PDF output streams.
    'output_eps_version' => 'PS_3_0_EPSF_3_0', // string | EPS format version for EPS output.
    'output_dxf_compatibility_level' => 'lines_and_arcs', // string | Level of primitive support for DXF output.
    'output_bitmap_anti_aliasing_mode' => 'anti_aliased', // string | Anti-aliasing mode for bitmap (PNG) output.
    'output_size_scale' => 3.4, // float | Overall uniform scaling factor for the output image.
    'output_size_width' => 3.4, // float | Output width, in the selected unit (see output.size.unit).
    'output_size_height' => 3.4, // float | Output height, in the selected unit (see output.size.unit).
    'output_size_unit' => 'none', // string | Measurement unit for output dimensions.
    'output_size_aspect_ratio' => 'preserve_inset', // string | How to preserve or stretch aspect ratio.
    'output_size_align_x' => 0.5, // float | Horizontal alignment (0.0 = left, 0.5 = center, 1.0 = right) when aspect ratio is preserved.
    'output_size_align_y' => 0.5, // float | Vertical alignment (0.0 = top, 0.5 = center, 1.0 = bottom) when aspect ratio is preserved.
    'output_size_input_dpi' => 3.4, // float | Override the detected DPI of the input image for size computations.
    'output_size_output_dpi' => 3.4, // float | DPI setting for the output image.
];

try {
    $result = $apiInstance->postDownload($associate_array);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling VectorizationApi->postDownload: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

Note: the input parameter is an associative array with the keys listed as the parameter names below.

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **image_token** | **string**| Image Token returned from a vectorize request with policy.retention_days &gt; 0. | |
| **receipt** | **string**| Receipt returned in the X-Receipt response header when upgrading a preview result to production. Include it when downloading additional formats from that upgraded preview. | [optional] |
| **output_file_format** | **string**| Output file format to generate. | [optional] [default to &#39;svg&#39;] |
| **output_shape_stacking** | **string**| Whether shapes are cut out of each other or stacked atop each other. | [optional] [default to &#39;cutouts&#39;] |
| **output_group_by** | **string**| Grouping of shapes in output. | [optional] [default to &#39;none&#39;] |
| **output_draw_style** | **string**| How shapes are rendered. | [optional] [default to &#39;fill_shapes&#39;] |
| **output_strokes_stroke_width** | **float**| Width of stroke for shape outlines (when enabled). | [optional] [default to 1] |
| **output_strokes_non_scaling_stroke** | **bool**| Use non-scaling strokes when drawing shape outlines. | [optional] [default to true] |
| **output_strokes_use_override_color** | **bool**| Override shape color with a specific color. | [optional] [default to false] |
| **output_strokes_override_color** | **string**| Color value to override shape stroke color if enabled. Must be in &#39;#RRGGBB&#39; or &#39;rgba(r,g,b,a)&#39; format. | [optional] [default to &#39;#000000&#39;] |
| **output_gap_filler_enabled** | **bool**| Enable filling small visual gaps caused by vector rendering artifacts. | [optional] [default to true] |
| **output_gap_filler_non_scaling_stroke** | **bool**| Use non-scaling strokes for gap filling. | [optional] [default to true] |
| **output_gap_filler_clip** | **bool**| Clip gap filler strokes to shape bounds when stacking shapes. | [optional] [default to false] |
| **output_gap_filler_stroke_width** | **float**| Width of the gap filler strokes (in output units). | [optional] [default to 2] |
| **output_parameterized_shapes_flatten** | **bool**| Whether to flatten detected circles, rectangles, and stars to curves. | [optional] [default to false] |
| **output_curves_line_fit_tolerance** | **float**| Maximum allowed error when approximating curves with line segments. | [optional] [default to 0.1] |
| **output_curves_allowed_quadratic_bezier** | **bool**| Allow quadratic Bézier curves in the output. | [optional] [default to true] |
| **output_curves_allowed_cubic_bezier** | **bool**| Allow cubic Bézier curves in the output. | [optional] [default to true] |
| **output_curves_allowed_circular_arc** | **bool**| Allow circular arcs in the output. | [optional] [default to true] |
| **output_curves_allowed_elliptical_arc** | **bool**| Allow elliptical arcs in the output. | [optional] [default to true] |
| **output_svg_version** | **string**| SVG version to declare in the SVG output. | [optional] [default to &#39;svg_1_1&#39;] |
| **output_svg_fixed_size** | **bool**| Whether to fix the SVG dimensions in the output file. | [optional] [default to false] |
| **output_svg_adobe_compatibility_mode** | **bool**| Enable Illustrator compatibility by disabling unsupported SVG features. | [optional] [default to false] |
| **output_pdf_version** | **string**| PDF version to generate for PDF output. | [optional] [default to &#39;PDF_1_4&#39;] |
| **output_pdf_compression_mode** | **string**| Compression method to apply to PDF output streams. | [optional] [default to &#39;Deflate&#39;] |
| **output_eps_version** | **string**| EPS format version for EPS output. | [optional] [default to &#39;PS_3_0_EPSF_3_0&#39;] |
| **output_dxf_compatibility_level** | **string**| Level of primitive support for DXF output. | [optional] [default to &#39;lines_and_arcs&#39;] |
| **output_bitmap_anti_aliasing_mode** | **string**| Anti-aliasing mode for bitmap (PNG) output. | [optional] [default to &#39;anti_aliased&#39;] |
| **output_size_scale** | **float**| Overall uniform scaling factor for the output image. | [optional] |
| **output_size_width** | **float**| Output width, in the selected unit (see output.size.unit). | [optional] |
| **output_size_height** | **float**| Output height, in the selected unit (see output.size.unit). | [optional] |
| **output_size_unit** | **string**| Measurement unit for output dimensions. | [optional] [default to &#39;none&#39;] |
| **output_size_aspect_ratio** | **string**| How to preserve or stretch aspect ratio. | [optional] [default to &#39;preserve_inset&#39;] |
| **output_size_align_x** | **float**| Horizontal alignment (0.0 &#x3D; left, 0.5 &#x3D; center, 1.0 &#x3D; right) when aspect ratio is preserved. | [optional] [default to 0.5] |
| **output_size_align_y** | **float**| Vertical alignment (0.0 &#x3D; top, 0.5 &#x3D; center, 1.0 &#x3D; bottom) when aspect ratio is preserved. | [optional] [default to 0.5] |
| **output_size_input_dpi** | **float**| Override the detected DPI of the input image for size computations. | [optional] |
| **output_size_output_dpi** | **float**| DPI setting for the output image. | [optional] |

### Return type

**\SplFileObject**

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `multipart/form-data`
- **Accept**: `image/svg+xml`, `application/postscript`, `application/pdf`, `application/dxf`, `image/png`, `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `postVectorize()`

```php
postVectorize($image, $image_url, $image_base64, $image_token, $mode, $input_max_pixels, $policy_retention_days, $processing_max_colors, $processing_shapes_min_area_px, $processing_palette, $processing_color_profile_input, $processing_color_profile_output, $processing_parameterized_shapes_ellipse_general_enabled, $processing_parameterized_shapes_ellipse_circle_enabled, $processing_parameterized_shapes_triangle_general_enabled, $processing_parameterized_shapes_triangle_isosceles_enabled, $processing_parameterized_shapes_quadrilateral_general_enabled, $processing_parameterized_shapes_quadrilateral_rectangle_enabled, $processing_parameterized_shapes_quadrilateral_bullet_enabled, $processing_parameterized_shapes_star_n3_enabled, $processing_parameterized_shapes_star_n4_enabled, $processing_parameterized_shapes_star_n5_enabled, $processing_parameterized_shapes_star_n6_enabled, $output_file_format, $output_shape_stacking, $output_group_by, $output_draw_style, $output_strokes_stroke_width, $output_strokes_non_scaling_stroke, $output_strokes_use_override_color, $output_strokes_override_color, $output_gap_filler_enabled, $output_gap_filler_non_scaling_stroke, $output_gap_filler_clip, $output_gap_filler_stroke_width, $output_parameterized_shapes_flatten, $output_curves_line_fit_tolerance, $output_curves_allowed_quadratic_bezier, $output_curves_allowed_cubic_bezier, $output_curves_allowed_circular_arc, $output_curves_allowed_elliptical_arc, $output_svg_version, $output_svg_fixed_size, $output_svg_adobe_compatibility_mode, $output_pdf_version, $output_pdf_compression_mode, $output_eps_version, $output_dxf_compatibility_level, $output_bitmap_anti_aliasing_mode, $output_size_scale, $output_size_width, $output_size_height, $output_size_unit, $output_size_aspect_ratio, $output_size_align_x, $output_size_align_y, $output_size_input_dpi, $output_size_output_dpi): \SplFileObject
```

Vectorize an image

Submit exactly one image source as multipart form data: image, image.url, image.base64, or image.token. The response body is the generated SVG, EPS, PDF, DXF, or PNG file selected by output.file_format. Clients should allow an idle timeout of at least 180 seconds.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = VectorizerAI\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new VectorizerAI\Api\VectorizationApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

$associative_array = [
    'image' => "/path/to/file.txt", // \SplFileObject | Binary file upload of the image to vectorize. Accepts .bmp, .gif, .jpeg, .png, or .tiff files.
    'image_url' => 'image_url_example', // string | URL to fetch the input image from for vectorization.
    'image_base64' => 'image_base64_example', // string | Base64-encoded string of the input image. Maximum size 1 megabyte.
    'image_token' => 'image_token_example', // string | An Image Token returned from an earlier vectorization call with policy.retention_days > 0.
    'mode' => 'production', // string | Mode of operation, useful during integration work.
    'input_max_pixels' => 2097252, // int | Maximum input image size (width × height in pixels) before resizing.
    'policy_retention_days' => 0, // int | Number of days to retain the uploaded image and its results for re-use.
    'processing_max_colors' => 0, // int | Maximum number of colors allowed in the vectorization result. 0 means unlimited.
    'processing_shapes_min_area_px' => 0.125, // float | Minimum shape area (in pixels) to keep in the result; smaller shapes are discarded.
    'processing_palette' => 'processing_palette_example', // string | Palette remapping and color control, using '[color][-> remapped][~ tolerance];' format.
    'processing_color_profile_input' => 'ignore', // string | How to handle ICC profiles embedded in input images.
    'processing_color_profile_output' => 'ignore', // string | ICC profile behavior for output files: preserve, ignore.
    'processing_parameterized_shapes_ellipse_general_enabled' => true, // bool | Enable detection and parameterization of this parameterized shape type.
    'processing_parameterized_shapes_ellipse_circle_enabled' => true, // bool | Enable detection and parameterization of this parameterized shape type.
    'processing_parameterized_shapes_triangle_general_enabled' => true, // bool | Enable detection and parameterization of this parameterized shape type.
    'processing_parameterized_shapes_triangle_isosceles_enabled' => true, // bool | Enable detection and parameterization of this parameterized shape type.
    'processing_parameterized_shapes_quadrilateral_general_enabled' => true, // bool | Enable detection and parameterization of this parameterized shape type.
    'processing_parameterized_shapes_quadrilateral_rectangle_enabled' => true, // bool | Enable detection and parameterization of this parameterized shape type.
    'processing_parameterized_shapes_quadrilateral_bullet_enabled' => true, // bool | Enable detection and parameterization of this parameterized shape type.
    'processing_parameterized_shapes_star_n3_enabled' => true, // bool | Enable detection and parameterization of this parameterized shape type.
    'processing_parameterized_shapes_star_n4_enabled' => true, // bool | Enable detection and parameterization of this parameterized shape type.
    'processing_parameterized_shapes_star_n5_enabled' => true, // bool | Enable detection and parameterization of this parameterized shape type.
    'processing_parameterized_shapes_star_n6_enabled' => true, // bool | Enable detection and parameterization of this parameterized shape type.
    'output_file_format' => 'svg', // string | Output file format to generate.
    'output_shape_stacking' => 'cutouts', // string | Whether shapes are cut out of each other or stacked atop each other.
    'output_group_by' => 'none', // string | Grouping of shapes in output.
    'output_draw_style' => 'fill_shapes', // string | How shapes are rendered.
    'output_strokes_stroke_width' => 1, // float | Width of stroke for shape outlines (when enabled).
    'output_strokes_non_scaling_stroke' => true, // bool | Use non-scaling strokes when drawing shape outlines.
    'output_strokes_use_override_color' => false, // bool | Override shape color with a specific color.
    'output_strokes_override_color' => '#000000', // string | Color value to override shape stroke color if enabled. Must be in '#RRGGBB' or 'rgba(r,g,b,a)' format.
    'output_gap_filler_enabled' => true, // bool | Enable filling small visual gaps caused by vector rendering artifacts.
    'output_gap_filler_non_scaling_stroke' => true, // bool | Use non-scaling strokes for gap filling.
    'output_gap_filler_clip' => false, // bool | Clip gap filler strokes to shape bounds when stacking shapes.
    'output_gap_filler_stroke_width' => 2, // float | Width of the gap filler strokes (in output units).
    'output_parameterized_shapes_flatten' => false, // bool | Whether to flatten detected circles, rectangles, and stars to curves.
    'output_curves_line_fit_tolerance' => 0.1, // float | Maximum allowed error when approximating curves with line segments.
    'output_curves_allowed_quadratic_bezier' => true, // bool | Allow quadratic Bézier curves in the output.
    'output_curves_allowed_cubic_bezier' => true, // bool | Allow cubic Bézier curves in the output.
    'output_curves_allowed_circular_arc' => true, // bool | Allow circular arcs in the output.
    'output_curves_allowed_elliptical_arc' => true, // bool | Allow elliptical arcs in the output.
    'output_svg_version' => 'svg_1_1', // string | SVG version to declare in the SVG output.
    'output_svg_fixed_size' => false, // bool | Whether to fix the SVG dimensions in the output file.
    'output_svg_adobe_compatibility_mode' => false, // bool | Enable Illustrator compatibility by disabling unsupported SVG features.
    'output_pdf_version' => 'PDF_1_4', // string | PDF version to generate for PDF output.
    'output_pdf_compression_mode' => 'Deflate', // string | Compression method to apply to PDF output streams.
    'output_eps_version' => 'PS_3_0_EPSF_3_0', // string | EPS format version for EPS output.
    'output_dxf_compatibility_level' => 'lines_and_arcs', // string | Level of primitive support for DXF output.
    'output_bitmap_anti_aliasing_mode' => 'anti_aliased', // string | Anti-aliasing mode for bitmap (PNG) output.
    'output_size_scale' => 3.4, // float | Overall uniform scaling factor for the output image.
    'output_size_width' => 3.4, // float | Output width, in the selected unit (see output.size.unit).
    'output_size_height' => 3.4, // float | Output height, in the selected unit (see output.size.unit).
    'output_size_unit' => 'none', // string | Measurement unit for output dimensions.
    'output_size_aspect_ratio' => 'preserve_inset', // string | How to preserve or stretch aspect ratio.
    'output_size_align_x' => 0.5, // float | Horizontal alignment (0.0 = left, 0.5 = center, 1.0 = right) when aspect ratio is preserved.
    'output_size_align_y' => 0.5, // float | Vertical alignment (0.0 = top, 0.5 = center, 1.0 = bottom) when aspect ratio is preserved.
    'output_size_input_dpi' => 3.4, // float | Override the detected DPI of the input image for size computations.
    'output_size_output_dpi' => 3.4, // float | DPI setting for the output image.
];

try {
    $result = $apiInstance->postVectorize($associate_array);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling VectorizationApi->postVectorize: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

Note: the input parameter is an associative array with the keys listed as the parameter names below.

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **image** | **\SplFileObject****\SplFileObject**| Binary file upload of the image to vectorize. Accepts .bmp, .gif, .jpeg, .png, or .tiff files. | [optional] |
| **image_url** | **string**| URL to fetch the input image from for vectorization. | [optional] |
| **image_base64** | **string**| Base64-encoded string of the input image. Maximum size 1 megabyte. | [optional] |
| **image_token** | **string**| An Image Token returned from an earlier vectorization call with policy.retention_days &gt; 0. | [optional] |
| **mode** | **string**| Mode of operation, useful during integration work. | [optional] [default to &#39;production&#39;] |
| **input_max_pixels** | **int**| Maximum input image size (width × height in pixels) before resizing. | [optional] [default to 2097252] |
| **policy_retention_days** | **int**| Number of days to retain the uploaded image and its results for re-use. | [optional] [default to 0] |
| **processing_max_colors** | **int**| Maximum number of colors allowed in the vectorization result. 0 means unlimited. | [optional] [default to 0] |
| **processing_shapes_min_area_px** | **float**| Minimum shape area (in pixels) to keep in the result; smaller shapes are discarded. | [optional] [default to 0.125] |
| **processing_palette** | **string**| Palette remapping and color control, using &#39;[color][-&gt; remapped][~ tolerance];&#39; format. | [optional] |
| **processing_color_profile_input** | **string**| How to handle ICC profiles embedded in input images. | [optional] [default to &#39;ignore&#39;] |
| **processing_color_profile_output** | **string**| ICC profile behavior for output files: preserve, ignore. | [optional] [default to &#39;ignore&#39;] |
| **processing_parameterized_shapes_ellipse_general_enabled** | **bool**| Enable detection and parameterization of this parameterized shape type. | [optional] [default to true] |
| **processing_parameterized_shapes_ellipse_circle_enabled** | **bool**| Enable detection and parameterization of this parameterized shape type. | [optional] [default to true] |
| **processing_parameterized_shapes_triangle_general_enabled** | **bool**| Enable detection and parameterization of this parameterized shape type. | [optional] [default to true] |
| **processing_parameterized_shapes_triangle_isosceles_enabled** | **bool**| Enable detection and parameterization of this parameterized shape type. | [optional] [default to true] |
| **processing_parameterized_shapes_quadrilateral_general_enabled** | **bool**| Enable detection and parameterization of this parameterized shape type. | [optional] [default to true] |
| **processing_parameterized_shapes_quadrilateral_rectangle_enabled** | **bool**| Enable detection and parameterization of this parameterized shape type. | [optional] [default to true] |
| **processing_parameterized_shapes_quadrilateral_bullet_enabled** | **bool**| Enable detection and parameterization of this parameterized shape type. | [optional] [default to true] |
| **processing_parameterized_shapes_star_n3_enabled** | **bool**| Enable detection and parameterization of this parameterized shape type. | [optional] [default to true] |
| **processing_parameterized_shapes_star_n4_enabled** | **bool**| Enable detection and parameterization of this parameterized shape type. | [optional] [default to true] |
| **processing_parameterized_shapes_star_n5_enabled** | **bool**| Enable detection and parameterization of this parameterized shape type. | [optional] [default to true] |
| **processing_parameterized_shapes_star_n6_enabled** | **bool**| Enable detection and parameterization of this parameterized shape type. | [optional] [default to true] |
| **output_file_format** | **string**| Output file format to generate. | [optional] [default to &#39;svg&#39;] |
| **output_shape_stacking** | **string**| Whether shapes are cut out of each other or stacked atop each other. | [optional] [default to &#39;cutouts&#39;] |
| **output_group_by** | **string**| Grouping of shapes in output. | [optional] [default to &#39;none&#39;] |
| **output_draw_style** | **string**| How shapes are rendered. | [optional] [default to &#39;fill_shapes&#39;] |
| **output_strokes_stroke_width** | **float**| Width of stroke for shape outlines (when enabled). | [optional] [default to 1] |
| **output_strokes_non_scaling_stroke** | **bool**| Use non-scaling strokes when drawing shape outlines. | [optional] [default to true] |
| **output_strokes_use_override_color** | **bool**| Override shape color with a specific color. | [optional] [default to false] |
| **output_strokes_override_color** | **string**| Color value to override shape stroke color if enabled. Must be in &#39;#RRGGBB&#39; or &#39;rgba(r,g,b,a)&#39; format. | [optional] [default to &#39;#000000&#39;] |
| **output_gap_filler_enabled** | **bool**| Enable filling small visual gaps caused by vector rendering artifacts. | [optional] [default to true] |
| **output_gap_filler_non_scaling_stroke** | **bool**| Use non-scaling strokes for gap filling. | [optional] [default to true] |
| **output_gap_filler_clip** | **bool**| Clip gap filler strokes to shape bounds when stacking shapes. | [optional] [default to false] |
| **output_gap_filler_stroke_width** | **float**| Width of the gap filler strokes (in output units). | [optional] [default to 2] |
| **output_parameterized_shapes_flatten** | **bool**| Whether to flatten detected circles, rectangles, and stars to curves. | [optional] [default to false] |
| **output_curves_line_fit_tolerance** | **float**| Maximum allowed error when approximating curves with line segments. | [optional] [default to 0.1] |
| **output_curves_allowed_quadratic_bezier** | **bool**| Allow quadratic Bézier curves in the output. | [optional] [default to true] |
| **output_curves_allowed_cubic_bezier** | **bool**| Allow cubic Bézier curves in the output. | [optional] [default to true] |
| **output_curves_allowed_circular_arc** | **bool**| Allow circular arcs in the output. | [optional] [default to true] |
| **output_curves_allowed_elliptical_arc** | **bool**| Allow elliptical arcs in the output. | [optional] [default to true] |
| **output_svg_version** | **string**| SVG version to declare in the SVG output. | [optional] [default to &#39;svg_1_1&#39;] |
| **output_svg_fixed_size** | **bool**| Whether to fix the SVG dimensions in the output file. | [optional] [default to false] |
| **output_svg_adobe_compatibility_mode** | **bool**| Enable Illustrator compatibility by disabling unsupported SVG features. | [optional] [default to false] |
| **output_pdf_version** | **string**| PDF version to generate for PDF output. | [optional] [default to &#39;PDF_1_4&#39;] |
| **output_pdf_compression_mode** | **string**| Compression method to apply to PDF output streams. | [optional] [default to &#39;Deflate&#39;] |
| **output_eps_version** | **string**| EPS format version for EPS output. | [optional] [default to &#39;PS_3_0_EPSF_3_0&#39;] |
| **output_dxf_compatibility_level** | **string**| Level of primitive support for DXF output. | [optional] [default to &#39;lines_and_arcs&#39;] |
| **output_bitmap_anti_aliasing_mode** | **string**| Anti-aliasing mode for bitmap (PNG) output. | [optional] [default to &#39;anti_aliased&#39;] |
| **output_size_scale** | **float**| Overall uniform scaling factor for the output image. | [optional] |
| **output_size_width** | **float**| Output width, in the selected unit (see output.size.unit). | [optional] |
| **output_size_height** | **float**| Output height, in the selected unit (see output.size.unit). | [optional] |
| **output_size_unit** | **string**| Measurement unit for output dimensions. | [optional] [default to &#39;none&#39;] |
| **output_size_aspect_ratio** | **string**| How to preserve or stretch aspect ratio. | [optional] [default to &#39;preserve_inset&#39;] |
| **output_size_align_x** | **float**| Horizontal alignment (0.0 &#x3D; left, 0.5 &#x3D; center, 1.0 &#x3D; right) when aspect ratio is preserved. | [optional] [default to 0.5] |
| **output_size_align_y** | **float**| Vertical alignment (0.0 &#x3D; top, 0.5 &#x3D; center, 1.0 &#x3D; bottom) when aspect ratio is preserved. | [optional] [default to 0.5] |
| **output_size_input_dpi** | **float**| Override the detected DPI of the input image for size computations. | [optional] |
| **output_size_output_dpi** | **float**| DPI setting for the output image. | [optional] |

### Return type

**\SplFileObject**

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `multipart/form-data`
- **Accept**: `image/svg+xml`, `application/postscript`, `application/pdf`, `application/dxf`, `image/png`, `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
