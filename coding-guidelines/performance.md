# WordPress Performance Coding Standards

These rules ensure that all WordPress code (themes and plugins) remains fast, scalable, and optimized for real-world users.  
All pull requests must comply with these performance best practices.

---

## 1. Database Queries

- ✅ **Use `$wpdb->prepare()`** for all custom SQL queries to avoid unnecessary overhead and ensure safety.
- ⚠️ **Avoid unindexed or repeated queries** inside loops — always cache or batch results.
- ⚡ **Leverage WordPress APIs** (e.g., `get_posts()`, `WP_Query`, `get_option()`) before writing raw SQL.
- 📦 Cache heavy queries using **transients** (`set_transient`, `get_transient`) or an **object cache** layer.
- 🚫 Do not use `SELECT *`; always fetch only the needed columns.

---

## 2. Asset Loading (CSS, JS, Images)

- ✅ Enqueue assets using `wp_enqueue_script` and `wp_enqueue_style` instead of hardcoding links.
- 📉 Combine and minify CSS and JS where possible.
- 💤 Load scripts **in the footer** (`in_footer => true`) unless absolutely required in the header.
- 🔄 Use **`wp_register_script`** to reuse the same handle instead of multiple enqueues.
- 🖼️ Always use **optimized images** (WebP preferred) and **`wp_get_attachment_image()`** for responsive image handling.

---

## 3. Server-Side Performance

- ⚙️ Avoid expensive PHP operations (like regex on large strings or recursive loops) inside hooks or templates.
- 🧠 Cache computed values when possible, especially in `shortcodes`, `widgets`, or `REST API` callbacks.
- 🔄 Use `wp_cache_get()` and `wp_cache_set()` when dealing with repetitive data.
- 🚫 Never use `file_get_contents()` or `curl_exec()` directly inside render logic. Use `wp_remote_get()` with proper caching.

---

## 4. Frontend Rendering

- ⏳ Reduce the number of HTTP requests — combine assets where feasible.
- 🪶 Remove unused scripts and styles via `wp_dequeue_script` / `wp_dequeue_style`.
- 🧩 Avoid inline `<style>` or `<script>` in templates; keep assets managed via enqueue.
- 🧍‍♂️ Use `the_excerpt()` instead of loading entire content where summaries are needed.

---

## 5. Hooks and Filters

- 🎯 Do not attach heavy callbacks to frequently executed hooks (`init`, `the_content`, `wp_head`).
- 🧹 Clean up registered hooks in plugin deactivation or theme switch hooks.
- ⚡ If a hook runs on every request, ensure its logic is constant-time (O(1)) or cached.

---

## 6. File and Template Structure

- 📂 Keep templates small and modular — avoid large, monolithic PHP files.
- 🧱 Use `get_template_part()` for reusable template fragments.
- 🧾 Avoid logic-heavy templates; push processing to helper functions or classes.

---

## 7. REST API and AJAX

- 🛡️ Cache API responses (using transients or object cache) when the data doesn’t change frequently.
- ⏱️ Validate and sanitize all inputs to avoid redundant data processing.
- 🧩 Use pagination for large data sets instead of returning all items at once.

---

## 8. Monitoring and Debugging

- 🧰 Use `WP_DEBUG_LOG` during development — never leave it enabled in production.
- 📊 Add logging only where necessary and remove before merging.
- 🚫 No `var_dump`, `print_r`, or `die` in production-ready code.

---

## 9. General Guidelines

- 🧾 Follow WordPress Coding Standards (PHPCS) with the `WordPress-Core` ruleset.
- ⚡ Always profile slow functions using tools like Query Monitor before merging.
- ✅ PR reviewers should check for any **potential slowdown in database queries or asset loading**.

---

**Version:** 1.0  
**Last Updated:** October 2025  
**Author:** ColoredCow
