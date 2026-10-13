// Supabase Edge Function: juso-eng
// 행정안전부 영문주소 API 중계 (브라우저 직접 호출이 CORS로 막힐 때만 사용)
//
// 배포:
//   supabase functions new juso-eng   → 이 파일 내용으로 index.ts 교체
//   supabase secrets set JUSO_ENG_KEY=발급받은_승인키
//   supabase functions deploy juso-eng --no-verify-jwt
// 변환기 설정 > 중계 주소:
//   https://<프로젝트ID>.supabase.co/functions/v1/juso-eng

const ALLOW_ORIGIN = "https://huey1002.github.io";

const cors = {
  "Access-Control-Allow-Origin": ALLOW_ORIGIN,
  "Access-Control-Allow-Methods": "GET, OPTIONS",
  "Access-Control-Allow-Headers": "*",
};

Deno.serve(async (req) => {
  if (req.method === "OPTIONS") return new Response(null, { headers: cors });

  const keyword = new URL(req.url).searchParams.get("keyword")?.trim() ?? "";
  if (!keyword) {
    return Response.json(
      { results: { common: { errorCode: "E0005", errorMessage: "검색어가 없습니다." }, juso: [] } },
      { headers: cors },
    );
  }

  const api = new URL("https://business.juso.go.kr/addrlink/addrEngApi.do");
  api.searchParams.set("confmKey", Deno.env.get("JUSO_ENG_KEY") ?? "");
  api.searchParams.set("currentPage", "1");
  api.searchParams.set("countPerPage", "10");
  api.searchParams.set("keyword", keyword);
  api.searchParams.set("resultType", "json");

  const r = await fetch(api);
  const body = await r.text();
  return new Response(body, {
    status: r.status,
    headers: { ...cors, "Content-Type": "application/json; charset=utf-8" },
  });
});
